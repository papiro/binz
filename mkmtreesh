#!/bin/sh

echo "(i)nit mtree or (c)ompare mtree?"
read cmd

getSeed () {
  echo "enter seed"
  read seed
}

case $cmd in
  "i")
    getSeed
    for i in bin sbin usr-bin usr-sbin usr-local-bin etc usr-local-etc; do
      p=/`echo $i | sed s!-!/!g`
      mtree -s $seed -p $p -c -K cksum,sha256 > /root/.${i}_chksum_mtree
      openssl enc -bf -salt -in /root/.${i}_chksum_mtree -out /root/.${i}_chksum_mtree.enc -e
      rm /root/.${i}_chksum_mtree
    done 
    ;;
  "c")
    getSeed
    for i in bin sbin usr-bin usr-sbin usr-local-bin etc usr-local-etc; do
      p=/`echo $i | sed s!-!/!g`
      openssl enc -bf -in /root/.${i}_chksum_mtree.enc -out /root/.${i}_chksum_mtree -d
      mtree -s $seed -p $p < /root/.${i}_chksum_mtree > /root/.${i}_chksum_mtree.output
      # if output is not empty, file has been changed
      if [ -s /root/.${i}_chksum_mtree.output ]; then
        echo "something's been changed..."
      else
        rm /root/.${i}_chksum_mtree
      fi
    done 
    ;;
  *) echo "enter i or c"
esac

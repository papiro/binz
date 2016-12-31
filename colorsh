#!/bin/bash

declare -A escapeSequences=(
# *** Text Colors *** #
  [black]="30m"
  [red]="31m"
  [green]="32m"
  [yellow]="33m"
  [blue]="34m"
  [magenta]="35m"
  [cyan]="36m"
  [default]="39m"
  [lightRed]="91m"
  [lightGreen]="92m"
  [lightYellow]="93m"
  [lightBlue]="94m"
  [lightMagenta]="95m"
  [lightCyan]="96m"

# *** Background Colors *** #
  [BGgreen]="42m"
  [BGyellow]="43m"
  [BGblue]="44m"
  [BGlightYellow]="103m"

# *** Formatting *** #
  [reset]="0m"
  [bold]="1m"
  [dim]="2m"
  [underline]="4m"
  [fillLine]="K"
)

for i in ${!escapeSequences[@]}; do
  declare ${i}=$(printf "\e[${escapeSequences[$i]}")
done

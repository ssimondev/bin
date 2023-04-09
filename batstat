#!/bin/sh
read -r CAPACITY < /sys/class/power_supply/BAT0/capacity
read -r STATUS < /sys/class/power_supply/BAT0/status

if [ "$CAPACITY" -gt 95 ]; then
    echo "Battery fully charged!"
fi

if [ "$STATUS" = "Charging" ] && [ "$CAPACITY" -le 95 ]; then
    echo "Charging at: $CAPACITY%"
fi

if [ "$STATUS" = "Discharging" ]; then
    if [ "$CAPACITY" -gt 20 ] && [ "$CAPACITY" -le 95 ]; then
	echo "Battery at: $CAPACITY%"
    fi
    if [ "$CAPACITY" -le 20 ]; then
        echo "Low battery: $CAPACITY%, connect the charger"
    fi
fi

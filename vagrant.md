### Remove all boxes
`for box in $(vagrant box list | awk '{print $1}'); do vagrant box remove $box; done;`

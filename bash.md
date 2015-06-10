Bash
----

#### Pretty print JSON response
`cmd |python -m json.tool`

#### Find big files
`sudo find / -type f -size +100000k -exec ls -lh {} \; | awk '{ print $9 ": " $5 }'`
`sudo du -chs /*`

#### INode count by dir
`for i in /*; do echo $i; find $i |wc -l; done`

#### repeat Curl and output response code
`for i in {0..500}; do curl -sL -w "%{http_code}\n" "http://127.0.0.1:8084/healthcheck" -o /dev/null; sleep .5; done;`

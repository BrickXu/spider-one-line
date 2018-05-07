# spider-one-line
一句话爬虫，基本没并发，基本没代理，纯粹自娱自乐，部分爬虫改一改可以继续爬同源内容，反正都是Linux shell，想用代理`export http_proxy`下就好了。

## KubeCon + CloudNativeCon North America 2017
```shell
curl -s --compressed  https://kccncna17.sched.com/ | egrep "<span class='event ev_\d+'><a href='.*' class" -o | awk -F "'" '{print $4}' | xargs -L 1 -I {} curl -s --compressed https://kccncna17.sched.com\{\} | egrep "<a class=\"file-uploaded file-uploaded-pdf\"" | awk -F "\"" '{print $4}' | xargs -P 10 -L 1 -I {} wget {}
```

## KubeCon + CloudNativeCon Europe 2018
```shell
curl -s --compressed  https://kccnceu18.sched.com/ | egrep "<span class='event .*'><a href='.*' class" -o | awk -F "'" '{print $4}' | xargs -L 1 -I {} curl -s --compressed https://kccnceu18.sched.com\{\} | egrep "<a class=\"file-uploaded file-uploaded-pdf\"" | awk -F "\"" '{print $4}' | xargs -P 10 -L 1 -I {} wget {}
```

## SNYK Vulnerability DB

W.I.P

```shell
PAGE=`curl -s https://snyk.io/vuln/\?packageManager\=all | grep -oE '<a class="pagination__link" href="/vuln/page/(\d+)"><span>(\d+)</span></a>' | awk 'END {print}' | grep -oE  '<span>(\d+)</span>' | grep -oE '\d+'`; for (( s=1; s<=$PAGE; s++ )) do curl -s --compressed "https://snyk.io/vuln/page/$s?packageManager=all" | wc -l; done
```

# spider-one-line
一句话爬虫

## KubeCon + CloudNativeCon North America 2017 Slides
```shell
curl -s --compressed  https://kccncna17.sched.com/ | egrep "<span class='event ev_\d+'><a href='.*' class" -o | awk -F "'" '{print $4}' | xargs -L 1 -I {} curl -s --compressed https://kccncna17.sched.com\{\} | egrep "<a class=\"file-uploaded file-uploaded-pdf\"" | awk -F "\"" '{print $4}' | xargs -P 10 -L 1 -I {} wget {}
```

## SNYK Vulnerability DB

Coming soon

```shell
```

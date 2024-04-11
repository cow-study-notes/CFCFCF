## 搜索域名+进入防火墙设置，这里组合链接直接到防火墙设置
### https://dash.cloudflare.com/a7a4cc3bf9dc7d4826cfd548e8c5cade/这里放域名/security/waf/custom-rules
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/d7706930-358e-4701-9626-e7a88a0d1ed8)
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/283d5e95-b535-4e32-9e1f-9f7abda61a74)
## 自定义规则
    SEO蜘蛛放行
        (cf.client.bot) or (http.user_agent contains "duckduckgo") or (http.user_agent contains "facebookexternalhit") or (http.user_agent contains "Feedfetcher-Google") or (http.user_agent contains "Mediapartners-Google") or (http.user_agent contains "msnbot") or (http.user_agent contains "TwitterBot") or (http.user_agent contains "yahoo")
        选择操作:跳过
        要跳过的 WAF 组件:所有其余自定义规则
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/995ce640-a201-4ea9-9b0e-6f2d46529cac)
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/dcd5288f-5d65-4522-b658-31215750c760)

## 拦截恶意流量
        (cf.threat_score ge 5 and not cf.client.bot) or (not http.request.version in {"HTTP/2" "HTTP/3"})
        选择操作:托管质询
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/beecef3f-7209-4c73-8617-a79e13bb3c3a)
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/69a45cf3-4707-4816-814e-f69d89f247fb)

## 速率限制规则
    导入规则
        (http.request.uri.path contains "/")
    速率限定 150次/10秒
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/2f4e3d34-c293-460a-861a-f3c6f6aeead8)
![image](https://github.com/cow-study-notes/CFCFCF/assets/105910804/3b5f7f5f-013f-4a48-9d5c-fb9bd0e62da6)


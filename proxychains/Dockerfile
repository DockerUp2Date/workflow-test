FROM dijedodol/simple-socks5-server
RUN apk update && apk upgrade && rm /var/cache/apk/* && apk add proxychains-ng && cat /etc/proxychains/proxychains.conf | grep -B 9999999 "\[ProxyList\]" > temp && mv temp /etc/proxychains/proxychains.conf
ENV PROXY_LIST=""
EXPOSE 1080
CMD ["sh", "-c", "echo \"$PROXY_LIST\" | tr , \\\\n | sed -e \"s/socks5 tor 9050/socks5 $(nslookup tor 2>/dev/null | grep 'Address 1' | cut -d ' ' -f3) 9050/g\" >> /etc/proxychains/proxychains.conf ; proxychains /app/simple-socks5-server/bin/simple-socks5-server"]
# TODO: automatically resolve any domain name

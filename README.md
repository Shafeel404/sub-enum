# sub-enum
Subdomain Enumeration
# /bin/bash
read -p "Enter a domain: " dom
echo "Finding subdomains using assetfinder"
assetfinder -subs-only $dom | tee subs.txt
sort -u subs.txt > sorted_subs.txt
echo "_______________________"
awk '{ printf "https://"; print }' sorted_subs.txt > abc.txt
while read kkb ; do
        curl -o /dev/null --silent --head --write-out "%{http_code} $kkb\n" "$kkb" >> jnm.txt
done < abc.txt
rm subs.txt
rm sorted_subs.txt
rm abc.txt

sed -i '/200/!d' jnm.txt
cat jnm.txt
rm jnm.txt

[![logo](https://github.com/lalatrade/lalatrade/blob/main/png/logo%231.png)](https://developer.aleo.org/)


<div style="text-align: center;">

[![Website](https://img.shields.io/badge/-Website-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)]( https://www.aleo.org/)
[![GitHub](https://img.shields.io/badge/-GitHub-1A4468?style=for-the-badge&logo=GitHub&logoColor=12141D)](https://github.com/AleoHQ)
[![Twitter](https://img.shields.io/badge/-Twitter-1A4468?style=for-the-badge&logo=Twitter&logoColor=1C9DEB)](https://twitter.com/AleoHQ)
[![Community Twitter](https://img.shields.io/badge/-Community_Twitter-1A4468?style=for-the-badge&logo=Twitter&logoColor=1C9DEB)](https://twitter.com/aleocommunity)
[![LinkedIn](https://img.shields.io/badge/-LinkedIn-1A4468?style=for-the-badge&logo=linkedin&logoColor=007BB6)](https://www.linkedin.com/company/aleohq/)
[![YouTube](https://img.shields.io/badge/-YouTube-1A4468?style=for-the-badge&logo=YouTube&logoColor=FF0000)]( https://www.youtube.com/channel/UCS_HKT2heOC_q88YQLiJt0g)
[![Community_Forum](https://img.shields.io/badge/-Community_Forum-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://community.aleo.org/)
[![Community_Calendar](https://img.shields.io/badge/-Community_Calendar-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://www.aleo.org/community/calendar)
[![Developer_Documentation](https://img.shields.io/badge/-Developer_Documentation-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://developer.aleo.org/)
[![Community_Blog](https://img.shields.io/badge/-Community_Blog-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://medium.com/@AleoHQ)
[![Announcements_Blog](https://img.shields.io/badge/-Announcements_Blog-1A4468?style=for-the-badge&logo=Website&logoColor=27A0D9)](https://www.aleo.org/blog)


</div>

Необходимо арендовать сервер с видеокартами. Сделать это можно на `https://vast.ai/`. Рекомендую арендовать `14х3090`. Сервера выбираем тут: `https://vast.ai/console/create/ `

Далее выполняем следующие команды:

```
sudo apt install nvidia-cuda-toolkit -y && \
wget http://nz2.archive.ubuntu.com/ubuntu/pool/main/o/openssl/libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb && \
sudo dpkg -i libssl1.1_1.1.1f-1ubuntu2.16_amd64.deb && \
wget https://github.com/damomine/aleominer/releases/download/v1.5.3/damominer_v1.5.3.tar && \
tar -xvf damominer_v1.5.3.tar && \
chmod +x damominer run_gpu.sh && \
apt install nano -y
```

```
sudo tee /root/run_gpu.sh > /dev/null <<EOF
#!/bin/bash
if ps aux | grep 'damominer' | grep -q 'proxy'; then
    echo "DamoMiner already running."
    exit 1
else
while ((1 <= 100))
do
    ./damominer \
        --address aleo..address \
        --proxy aleo1.damominer.hk:9090
    sleep 3
done
fi
EOF
```

```
./run_gpu.sh
```

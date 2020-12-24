Memcached [in-memory data store] as a microservice in Docker
====================================================

* ***Actions on the deployment of the project:***

- Making a new project memcached_anasir.loc:
				
		sudo chmod -R 777 /var/www/Memcached/memcached_anasir.loc

		//!!!! .conf
		sudo cp /etc/apache2/sites-available/test.loc.conf /etc/apache2/sites-available/memcached_anasir.loc.conf
				
		sudo nano /etc/apache2/sites-available/memcached_anasir.loc.conf

		sudo a2ensite memcached_anasir.loc.conf

		sudo systemctl restart apache2

		sudo nano /etc/hosts
		
		cd /var/www/Memcached/memcached_anasir.loc
		
Deploy project:

- Download the archieve with project files( Code -> Download ZIP ).		

* ***Actions:***

	sudo docker-compose up

Error related with using the wrong Compose file version:

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/_1.png )

Error: "Error starting userland proxy: listen tcp 0.0.0.0:11211: bind: address already in use"

_It happens that other containers can use this port. In this case, using the command to remove all containers will help:_
	
	docker rm -f $(docker ps -aq)
	
[Docker bind error: address is already in use]( https://coderoad.ru/37971961/Docker-%D0%BE%D1%88%D0%B8%D0%B1%D0%BA%D0%B0-%D0%BF%D1%80%D0%B8%D0%B2%D1%8F%D0%B7%D0%BA%D0%B8-%D0%B0%D0%B4%D1%80%D0%B5%D1%81-%D1%83%D0%B6%D0%B5-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D1%83%D0%B5%D1%82%D1%81%D1%8F )	

_In my case, the service was started, I had already used Memcached earlier in other projects, and the port was therefore busy. Accordingly, we will stop the service and restart:_

[Error starting userland proxy: listen tcp 0.0.0.0:11211: bind: address already in use]( https://serverfault.com/questions/1004078/memcache-container-error-starting-userland-proxy-listen-tcp-0-0-0-011211-bin )

	sudo systemctl status memcached	
	sudo systemctl stop memcached
	sudo docker-compose up
	
![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/_2.png )

In another terminal:
	
	cd /var/www/Memcached/memcached_anasir.loc
	telnet localhost 11211

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/_3.png )

---

Ahsan Nasir

[Memcached [in-memory data store] as a microservice in Docker - Docker #11 (10:00)]( https://www.youtube.com/watch?v=a-srbTk5Xv8&ab_channel=AhsanNasir )

In this video, i present Memcached, a distributed; in-memory caching service running in docker as a container. Jump to code 
[2:50.]( https://youtu.be/a-srbTk5Xv8?t=170 )

Memcached is expected to have a response time of about ~2ms giving extreme performance to your cloud based applications.
The memcached can further be scaled by distributing it over several servers/containers to increase caching performance.
We will get into much details for this in the video! Please support my channel, Thank you!

[(4:10)]( https://youtu.be/a-srbTk5Xv8?t=250 )

	sudo docker-compose up

[(5:07)]( https://youtu.be/a-srbTk5Xv8?t=307 )

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/1.png )

[(5:30)]( https://youtu.be/a-srbTk5Xv8?t=330 )

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/2.png )

[(6:47)]( https://youtu.be/a-srbTk5Xv8?t=407 )

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/3.png )

[(7:55)]( https://youtu.be/a-srbTk5Xv8?t=475 )

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/4.png )

[(8:51)]( https://youtu.be/a-srbTk5Xv8?t=531 )

![screenshot of sample]( https://github.com/mslobodyanyuk/memcached_anasir/blob/master/public/images/5.png )

#### useful links:

<https://memcached.org/>

Github repo: 

https://github.com/ahsannasir/docker_tut_yt

https://www.journaldev.com/16/memcached-telnet-commands-example

[Error starting userland proxy: listen tcp 0.0.0.0:11211: bind: address already in use]( https://serverfault.com/questions/1004078/memcache-container-error-starting-userland-proxy-listen-tcp-0-0-0-011211-bin )

[Docker bind error: address is already in use]( https://coderoad.ru/37971961/Docker-%D0%BE%D1%88%D0%B8%D0%B1%D0%BA%D0%B0-%D0%BF%D1%80%D0%B8%D0%B2%D1%8F%D0%B7%D0%BA%D0%B8-%D0%B0%D0%B4%D1%80%D0%B5%D1%81-%D1%83%D0%B6%D0%B5-%D0%B8%D1%81%D0%BF%D0%BE%D0%BB%D1%8C%D0%B7%D1%83%D0%B5%D1%82%D1%81%D1%8F )

_Also can be useful information in:_

Traversy Media

[Intro To Memcached]( https://www.youtube.com/watch?v=7MLXuG83Fsw&ab_channel=TraversyMedia )

Quick Notepad Tutorial

[Example to use Memcached on PHP ( Memcached - Use it on PHP )]( https://www.youtube.com/watch?v=_wbuByP2HYs&ab_channel=QuickNotepadTutorial )

Артем Манченков

[GeekBrains PHP 2 [Memcached]]( https://www.youtube.com/watch?v=5q4VoOOlwXw&ab_channel=%D0%90%D1%80%D1%82%D0%B5%D0%BC%D0%9C%D0%B0%D0%BD%D1%87%D0%B5%D0%BD%D0%BA%D0%BE%D0%B2 )
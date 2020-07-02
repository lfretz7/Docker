OSS Ticket
==========

## Übersicht 

    +---------------------------------------------------------------+
    ! Container: apache2                                            !	
    +---------------------------------------------------------------+
    ! Container-Engine: Docker                                      !	
    +---------------------------------------------------------------+
    ! Gast OS: Ubuntu 16.04                                         !	
    +---------------------------------------------------------------+
    ! Hypervisor: Hyper-V                                           !	
    +---------------------------------------------------------------+
    ! Host-OS: Windows                                              !	
    +---------------------------------------------------------------+
    ! Notebook - privates Netz 192.168.0.204                        !                 
    +---------------------------------------------------------------+


## Netzwerkplan
    +---------------------------------------------------------------+
    !                                                               !                 
    ! Zugang: 8080 (192.158.55.101:80)                              !	
    !                                                               !	
    !    +--------------------+          +---------------------+    !
    !    ! privater Laptop    !          ! Apache Server       !    !       
    !    ! Host: NB-IT-120010 !          ! Host: default Docker!    !
    !    ! IP: 192.168.0.204  ! <------> ! IP: 172.17.0.2      !    !
    !    !                    !          ! Port 80             !    !
    !    !                    !          ! Nat: 8080           !    !
    !    +--------------------+          +---------------------+    !
    !                                                               !	
    +---------------------------------------------------------------+

## Beschreibung

Dieser Container beinhaltet einen Apache-Server, der als index.html Seite
einen Onlineshop zur Verfügung stellt.

Der Ordner "public-html" kann angepasst werden und die Änderungen werden
vom Container übernommen


## Administration

**Navigieren und builden:**

```cd C:\Data\Berufsschule\Modul 300\Github_Repositories\MeineLokalenRepositories\Docker```
```docker build -t my-apache2 .```
	
**Starten:**

```docker run -dit --name my-running-app -p 8080:80 my-apache2```


**Webseite:**

[http://localhost:8080](http://localhost:8080)
	

	
### Docker Repositories

* [Apache](https://github.com/mc-b/M300/tree/master/docker/apache)


## Docker verwendete Befehle

#### Aktive und beendete Container anzeigen (all):
```docker ps -a```


#### Container stoppen, killen
```container stop (Container-ID)```
```container kill (Container-ID)```


#### Alle beendeten Container löschen:
```docker rm `docker ps -a -q```

#### Funktionsfähigkeit überprüfen Host -> Docker Container:
```curl http://localhost:8080```	

Es muss der Inhalt von web/index.html angezeigt werden.


#### IP-Adresse des Containers herausfinden:
```docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' (Container-ID)```






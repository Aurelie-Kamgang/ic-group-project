# Ic Group Project
### Containerisation of the web application.
1. Clone the repos
`git clone [https://github.com/sadofrazer/ic-webapp.git](https://github.com/sadofrazer/ic-webapp.git)`

2. Build the image:
`docker buitd -t ic-webapp:v1.0 .`

![](https://lh5.googleusercontent.com/hg5Pmt82WY8TAUZpdBIo9rsjSscTYT1oV4O0sAp5ZXGfsw0pW5puMOS1EoAw7TPoZckyiJf70uO4-fA5qMvGmLBxMsjQV2tWVqVA7dhSTDR_MnIu4yenW8PgL2Ir46EuUwZG-Pw4CzgJqh8r1EhXRGKj1ABfjq0idhr-FlDtkIclVpzQ-YCoPtYcMw)

![](https://lh3.googleusercontent.com/nigJ3Bs2Hth7dBNcuV1YpOVZjCCyfxF6T-aSRbXrlBbNq6hl0WyFTVLiPYGEhY0Lto2dhBcbF2l0aujuALBiKG9F6zyydRNdg6cwMW2LHMwxFmTpZ_5f8uN8JV6MJo1krJqactn3WmQpsD-QXOjiqp13nlKOAv64TgsG6B9d3R78y2aRrT4MSWPHzw)
3. launch a test container allowing to go on the official websites of each of applications:

![](https://lh6.googleusercontent.com/aZRdQhThLr_jCPJOqsdtYRCgBCGf1lrr7es-4PjynywVATVxdouumlRsDsQ_CcFUOtvBHkgBHp1IA7WNElMczLhks181kyzLyLrB0LiOGf7NO5V9N20gm-bhlI4Ms7qyqyWCcqmAix7BwUNgfSvVrv3B7azr2mvL57lwUPhiY8nOdLmcbaTivHokbg)

![](https://lh6.googleusercontent.com/Dfxl4FFxHCVyjVZVeTpbSI1Z01d7JIEDST5_auzRKHJ3nCfN78vWcL3-fnfaVTRTMliJcOmW-bMpvYkep-t2ro5CRsZiW7hr_3Jp7ryfKD-UeYFhg4NnJ24AFtak25svcObwJMEL39oegjawF1r_YzJ-YdP698j1J4Pjz6SCHkys6yOdPcxBRi38dg)
4. push image to  Docker hub registry:
	- Tag the image:
	`docker tag ic-webapp:v1.0 blondel/ic-webapp:v1.0`

![](https://lh5.googleusercontent.com/JXKaelTQQAxPX_M0VRSYxFTHiSE1ryqzBVPiLStiHxxF6oF-d6gbUGNT_aS2DAfan-vtYySEwrRf0M6IRUqUN_nX3uzh6FZNtFT__i1AoWt29FO0sdXIE2YxJMiOP488agGKayNoLZ-SIsLwIe6B4kZffwQZLj7nE376IH0vEF-AlHqGzWNjs1qbHQ)
	- Push the image:
	`docker push blondel/ic-webapp:v1.0`

![](https://lh4.googleusercontent.com/nI-WeW0gFJaqHCRy0n6J9BcnG6N7w9G8I_ZiBaHxbWBj0TmQtJ0414PtArkopx5-sDb7fD0r8KSfo4MSk1NN-6aHVIeeIU49N8uvBqatT9_SNJMoW6iXYRTCdme8R4CVcZOSxu-FesNbqi_JbERmPjoxNs3miM14EaHI0wqMB22RaMH5SDKxBAvo7Q)
![](https://lh3.googleusercontent.com/m_cUiWVEhpJ2N5IwjnSQgm1D7TJ8wmGJEsz3ZjXoEmSvl1Fs2lnEWW7vyUDm66pLs3rQUXIrwn7kcgYjPt_B52rLOmoewRHsOUNFqOtZjYss80on0N3gwzj86Ko969pXTACe-cYQqUB2lGPYXGQb04MTHDBG_kAGOs7lqVD7pzoirMdIVJmtGZP3Rg)

### Part 1: Deploying different applications in a Kubernetes cluster.

a. Architecture:
 type and role of each resource (A...H) mentioned in this architecture.
![](https://lh3.googleusercontent.com/Vf-PRFcXNR9PJ_dul0yod3uql2U538NXUaVAX3fzP-PL9MLkdMkW10PWvNoD_pd7EhGBCieVRH_Vr9nDP8HWa-K_KOKl71bTb3DQ6pH_vvyBad0Eq9mONEINlhTKYftYgsp5sgQJ-BK-LkxeDHHaPwIjf312elCyAnWcY5F5OHB-J6UsJzbTRl-TzQ)
A

Type of Ressource= Service ic-webapp (frontend)

Role= exposes the web application ic-webapp

B

Type of Ressource= ic-webapp application 

Role= containerised the odoo application and pgadmin

C

Type of Ressource=  Odoo Web Service

Role= exposes the Odoo website

D

Type of Ressource=  Odoo Application

Role= Multi-purpose ERP that manages sales, purchasing, accounting, inventory, personnel …

E

Type of Ressource=  BDD_Odoo Service

Role= exposes the BDD_Odoo application

F

Type of Ressource= odoo database application (backend)
Rfle= store data from the Odoo application through the Pgadmin GUI
G

Type of Ressource= Pgadmin Service 

Role= exposes the Pgadmin application

H

Type of Ressource=  Pgadmin Application

Role= Graphical administration of the PostgreSQL database



b. Deployment of the Odoo application
	- Create folders for data on the host:
	`mkdir /data/odoo`
	`mkdir /data/postgres`
      - Apply deployment and service of postres: `kubectl apply -f postgres.yml`
      - Apply  deployment and service of odoo: `kubectl apply -f odoo.yml`

![](https://lh3.googleusercontent.com/zHvj6L_1vPVd2kU7Ey-Os4akWGgNQ0ZYQ6GZqXuxNiZnfUrqfO_IpLz71XQctyKi1CiNBZ3TnvKGb4SJHINkclDTfv1SYLxHLxPjh1zDt4dLIj5EePcKimRtbfHNzyWqix9xCa-3JE8ubvSSsnK-KMbHVFhPPBsjrRuTlEMUzznq5R-Cx54JGCGXdA)


Verification:

![](https://lh5.googleusercontent.com/kiBzVC_upaAMqcMVZtHuXUAQll6Uu1WHYJvZK0GqmBKaPX4H0km7j0OhjKiZGEBmZYKtK82djVx4-4B-U-BrgYMeoHIAmiN7s8CgVYIlev11zZMHtym7t6ZxOGI2Du1xpO8MuxYDuOIaMPFdfYqmr3L1ifIRMxXUhgwLSFNi0N0IYTMJHAee2S4U8w)


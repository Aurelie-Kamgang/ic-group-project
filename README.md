# DEVOPS
### Conteneurisation de l’application web.
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

Type de Ressource= Service ic-webapp (frontend)

Rôle= accès à l’application web ic-webapp

B

Type de Ressource= application ic-webapp

Rôle= conteneurisé l’application odoo et pgadmin

C

Type de Ressource= Service web Odoo

Rôle= accès au site web d’Odoo

D

Type de Ressource= Application Odoo

Rôle= ERP multi usage qui permet de gérer les ventes, les achats, la comptabilité, l’inventaire, le personnel …

E

Type de Ressource= Service BDD_Odoo

Rôle= accès à l’application BDD_Odoo

F

Type de Ressource= application de la base de donnée d’odoo (backend)

Rôle= stocker les données de l’application Odoo à travers l’interface graphique de Pgadmin

G

Type de Ressource= Service Pgadmin

Rôle= accès à l’application Pgadmin

H

Type de Ressource= Application Pgadmin

Rôle= administrer de façon graphique la base de données PostgreSQL


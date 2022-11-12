
## Steps to follow
This short tutorial explains step by step how to implement the red thread project

## Prerequisites

- Have **docker**,*docker-compose*, **k8s** and **Jenkins** on your workstation to provision the lab locally


### Build, test (**docker**) and deploy the application (**kubernetes**)

### Build, test and push the Docker image

- To see the procedure to deploy the application using kubernetes go to the readme of the Manifests_k8s folder 

- To see the procedure for deploying the application using docker-compose go to the readme of the docker-ressources folder

## CI with Jenkins

#### Launch the Jenkins
#### Retrieve the token for the GUI and create your account
Type the following command on the Jenkins vm
> docker exec -it jenkins_jenkins_1 cat /var/jenkins_home/secrets/initialAdminPassword

Once the token is retrieved, connect to the Jenkins GUI on port 8080 and insert the token.

#### Jenkins plugins to install
- Docker
- Docker Pipeline
- docker-build-step

![](https://lh5.googleusercontent.com/g0vujbJyXRjL1jWLNdHTl8xlMpfAgEIygRu6T_pAnlohpDF90UkB0WtEYuCTx7mMMggnOsAE9g75rgQYRoh6hy8_769ZqA70YGBDdpiUaqt8bGAk8cJLkhP1uJuWbQIwXEPTb2ji0VCcB-TFvsPNLxsc9Bjb3ezWOPY1PWa_zapZFVwNnFDbgOfjOg)




#### Characteristics of the Pipeline job 
##### Secret and parameters

|Type |Default Value |Description |
|                   |Type              |Default Value    |Description                   |
|-------------------|------------------|-----------------|------------------------------|
|    snyk_token     | secret text      |      N/A        | token de connexion à snyk    |
| dockerhub_password| secret text      |      N/A        | Password dockerhub           |
|    IMAGE_TAG      | Paramètre du job |      v1.0       | tag de l'image docker        |
|  DOCKERFILE_NAME  | Paramètre du job | Dockerfile_v1.0 | Dockerfile à utiliser        |
|      HOST_IP      | Paramètre du job |   127.0.0.1     | adresse IP de la machine hote|
|  APP_EXPOSED_PORT | Paramètre du job |      8000       | Port expose de l'appli       |


**![](https://lh4.googleusercontent.com/Kv_YJ-S8RDUaTjOIJ1cVO87vTuAVLghyjD-F9HkayZMQqkO0MHgN59zicnvDfqSxnMy2FVJAJdhZAyfCkDoCvjLGAH3pqWsmph3Ml9chDqUL7QvO8di2zvA31oBBu0XVITQewh0OdzzBCtzXYJPC_jsH9J5Vebs_CTgyWo35S-QR2uYKkC-xhimqPbcRaA)**
**![](https://lh4.googleusercontent.com/sLN_Ser1vGWtkdYpjO3JZ7S2bypk7qO3hM8VuhBZJU8A89r7YiDeakYHmDvWchwyE1kQwaI0s_aHLCtUvH0PTQT_tLhjXPHIkWxBQl9slKz8NDqDTlZ068Nk9Fnm28Iov0YpSWua-2iPqSiKjKaDtmTHZJ56oiFVVZymJGxBjTsveAabDP_sLEjDTfKsUw)**
**![](https://lh4.googleusercontent.com/thpA_qFblD_OEkc9YuyejHJrDQ43s4d-TFT25Pz7g5FErD6uXQL4f0fCFn4rO2pmjl814EwLBLi1Pau1A7PZaWEdF6lFSBKwaKh9dl8o9AXTxHEoCMKz_hSUgB2HcL4RR5V_fRqM8auau_0_AQyuVjid_rawtdPsQJ_Kf_J0WNkLBH2Bd2tBsRgHUYNG9g)**


 #### Configure the system
 - Configure docker build
**![](https://lh5.googleusercontent.com/Irl2t-vcsHrj31LlMd3H1s2jGVgEInu23Fx9Jc0HWkr-wErRey0fQbZf-HA1j1kI6yVYt75p7_3zN8kZgBPeDr3jkE8RVwoZifOj_GsHYbf_88y01rgC0FxyDWm4DkwBB0I_cemqUoToZvPGk7tYskUSJlhTTwJshauBoZ_bCYi4Liysf8c0ZnLrC8vZRA)**
- Configure Global librarie
**![](https://lh4.googleusercontent.com/lf8Ssqee-S8kgr_A6b40KJvfdpV9o9O9b5ky8Y-LitVC9IiQ_Fq7k-MTMpfalUPlRGy_ZVUB_1JuJkbvuAZPJy1tmvP6BuiMA-MGJLRR0OtU8lVm9M3Mi82PHSuwkGLiXzFDK6I-zb3hoZarYxkx_ud7fxZXxrCfvrV3UvYngM2Vq0FK2RfLGP5afXOTbw)**
- Configure Slack
**![](https://lh3.googleusercontent.com/XGQHzBuUJqAo7KmU0VEmGQVwB403plUl0VT9ywpdLRNgZROnyzPIPnrQLl3feJEY7GioC2tajG_ph-WlNAJ05vPWH1apuqelTfR8eAcmpffd19RbHJYxQn0VqEwoTVu4Q5hqjMN7oaN24k-0r0gPWpbXti55GSvNezvWhvDg51v3TBUTjRoUKo8hw_MDtg)**
**![](https://lh5.googleusercontent.com/NXp-YFt7Ar7tWcdlLThZc8hpWoPhvZAUWiTurunZUPqprXwOfYMF6IkSaYWjjxcO2DCJOQfmTAr3f-9J9kYZFFXbmxqHHdvhNw-MqG4FAr4CIy8FVn4Tb6lKvarbdePm88BIsuUc6R0vRogy2X7Vgi2BCZBiZHkhIc-3wCSK44fLXK4VOWCSnCdh2DMfMQ)**

#### webhook (To be configured in Github)
**![](https://lh6.googleusercontent.com/X7Pk08zmOMm-kOkQ11QTKhhprGhykg3j2HrvOQtwJDqKXS4WIPyNaiX5CcorSI0yuHteqI21wnyVQVWEsAXytwcfpgIql8CTGSYu2kt6y6T7X-p1ehCt9_OMGgywiMa85UPwS4DQRaYcJDzVpj2Wu8dwpxJ-tX-pVTv-b-pS-lkupG4jyIPAYu6AfkZ5dQ)**
Pipelne: 
    - Definition : Pipeline script from SCM > GIT
        - Branch : */main
        - Script Path : Jenkinsfile
        
#### Lauch the pipeline
**![](https://lh4.googleusercontent.com/96xi-ZxPFgrTSPJcNOMFVgNx238fKf6BBjM40ttYxrJEgzce_tPfTYu2_N3fZoyUd4xz5oPbOpzq4-FEEmE8LEWXYFKk4VmX-HV0ayhcak_s6Axxqa1GMmS_yq4oqvQFaMEywh3kEDUby3Avs5avaExdhe4nZAkIaXc84PXXG9wA0yRPIvCWVdTF73xpMA)**
**![](https://lh4.googleusercontent.com/tpMVgyinE0QRKPL9o3AjDnfTPLrwObzVMuHUDRjoOCzJElBKFNTHb_qiwiVISpvuh6-mMsqvVbYhj_PfW7vvW7nmUW4J2xNv6Pix0GHAzih4lkk8j9ESc45z7oiGjg6i4g61wVTt7IOjA5kZ_wHxCgKv0B-wam1DALQhGqCzwKuKbIjgkluUZTFTWvn1dQ)**

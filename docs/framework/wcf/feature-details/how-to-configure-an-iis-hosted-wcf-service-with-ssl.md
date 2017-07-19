---
title: "Proc&#233;dure&#160;: configurer un service WCF h&#233;berg&#233; par IIS avec SSL | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: df2fe31f-a4bb-4024-92ca-b74ba055e038
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# Proc&#233;dure&#160;: configurer un service WCF h&#233;berg&#233; par IIS avec SSL
Cette rubrique décrit comment installer un service WCF hébergé par IIS pour utiliser la sécurité de transport HTTP.  La sécurité de transport HTTP requiert un certificat SSL à enregistrer avec IIS.  Si vous n'avez pas de certificat SSL, vous pouvez utiliser IIS pour générer un certificat de test.  Vous devez ensuite ajouter une liaison SSL au site Web et configurer les propriétés d'authentification du site Web.  Enfin, vous devez configurer le service WCF pour utiliser HTTPS.  
  
### Création d'un certificat auto\-signé  
  
1.  Ouvrez le Gestionnaire des services IIS \(inetmgr.exe\), puis choisissez le nom de votre ordinateur dans l'arborescence à gauche.  Du côté droit de l'écran, sélectionnez Certificats de serveur.  
  
     ![Écran d'accueil du Gestionnaire des services IIS](../../../../docs/framework/wcf/feature-details/media/mg-inetmgrhome.jpg "mg\_INetMgrHome")  
  
2.  Dans la fenêtre Certificats de serveur, cliquez sur **Créer un certificat auto\-signé**. Lien.  
  
     ![Création d'un certificat auto&#45;signé avec IIS](../../../../docs/framework/wcf/feature-details/media/mg-createselfsignedcert.jpg "mg\_CreateSelfSignedCert")  
  
3.  Entrez un nom convivial pour le certificat auto\-signé et cliquez sur **OK**.  
  
     ![Boîte de dialogue Créer un certificat auto&#45;signé](../../../../docs/framework/wcf/feature-details/media/mg-mycert.jpg "mg\_MyCert")  
  
     Les détails du certificat auto\-signé nouvellement créé sont maintenant affichés dans la fenêtre **Certificats de serveur**.  
  
     ![Fenêtre Certificat de serveur](../../../../docs/framework/wcf/feature-details/media/mg-servercertificatewindow.jpg "mg\_ServerCertificateWindow")  
  
     Le certificat généré est installé dans le magasin d'Autorités de certification racines de confiance.  
  
### Ajouter une liaison SSL  
  
1.  Toujours dans le Gestionnaire des services IIS, développez le dossier **Sites**, puis le dossier **Site Web par défaut** dans l'arborescence de la partie gauche de l'écran.  
  
2.  Cliquez sur **Liaisons...**. Lien dans la section **Actions** dans la partie supérieure droite de la fenêtre.  
  
     ![Ajout d'une liaison SSL](../../../../docs/framework/wcf/feature-details/media/mg-addsslbinding.jpg "mg\_AddSSLBinding")  
  
3.  Dans la fenêtre Liaisons de sites, cliquez sur le bouton **Ajouter**.  
  
     ![Boîte de dialogue Liaisons du site](../../../../docs/framework/wcf/feature-details/media/mg-sitebindingsdialog.jpg "mg\_SiteBindingsDialog")  
  
4.  Dans la boîte de dialogue **Ajouter la liaison de site**, sélectionnez https pour le type et le nom convivial du certificat auto\-signé que vous venez de créer.  
  
     ![Exemple de liaison de site](../../../../docs/framework/wcf/feature-details/media/mg-mycertbinding.jpg "mg\_MyCertBinding")  
  
### Configurer le répertoire virtuel pour SSL  
  
1.  Toujours dans le Gestionnaire des services IIS, sélectionnez le répertoire virtuel qui contient votre service sécurisé WCF.  
  
2.  Dans le volet central de la fenêtre, sélectionnez **Paramètres SSL** dans la section IIS.  
  
     ![Paramètres SSL pour le répertoire virtuel](../../../../docs/framework/wcf/feature-details/media/mg-sslsettingsforvdir.jpg "mg\_SSLSettingsForVDir")  
  
3.  Dans le volet Paramètres SSL, activez la case à cocher **Exiger SSL** et cliquez sur le lien **Appliquer** dans la section **Actions** de la partie droite de l'écran.  
  
     ![Paramètres SSL pour le répertoire virtuel](../../../../docs/framework/wcf/feature-details/media/mg-vdirsslsettings.JPG "mg\_VDirSSLSettings")  
  
### Configurer le service WCF pour la sécurité de transport HTTP  
  
1.  Dans le fichier web.config du service WCF, configurez la liaison HTTP pour utiliser la sécurité de transport, comme indiqué dans le code XML suivant.  
  
    ```  
    <bindings>  
          <basicHttpBinding>  
            <binding name="secureHttpBinding">  
              <security mode="Transport">  
                <transport clientCredentialType="None"/>  
              </security>  
            </binding>  
          </basicHttpBinding>  
        </bindings>  
  
    ```  
  
2.  Spécifiez votre service et point de terminaison de service comme indiqué dans le code XML suivant.  
  
    ```  
    <services>  
          <service name="MySecureWCFService.Service1">  
            <endpoint address=""  
                      binding="basicHttpBinding"  
                      bindingConfiguration="secureHttpBinding"  
                      contract="MySecureWCFService.IService1"/>  
  
            <endpoint address="mex"  
                      binding="mexHttpsBinding"  
                      contract="IMetadataExchange" />  
          </service>  
        </services>  
  
    ```  
  
## Exemple  
 Voici un exemple complet d'un fichier web.config pour un service WCF utilisant la sécurité de transport HTTP.  
  
```  
<?xml version="1.0"?>  
<configuration>  
  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <services>  
      <service name="MySecureWCFService.Service1">  
        <endpoint address=""  
                  binding="basicHttpBinding"  
                  bindingConfiguration="secureHttpBinding"  
                  contract="MySecureWCFService.IService1"/>  
  
        <endpoint address="mex"  
                  binding="mexHttpsBinding"  
                  contract="IMetadataExchange" />  
      </service>  
    </services>  
    <bindings>  
      <basicHttpBinding>  
        <binding name="secureHttpBinding">  
          <security mode="Transport">  
            <transport clientCredentialType="None"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <!-- To avoid disclosing metadata information, set the value below to false and remove the metadata endpoint above before deployment -->  
          <serviceMetadata httpsGetEnabled="true"/>  
          <!-- To receive exception details in faults for debugging purposes, set the value below to true.  Set to false before deployment to avoid disclosing exception information -->  
          <serviceDebug includeExceptionDetailInFaults="false"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
    <serviceHostingEnvironment multipleSiteBindingsEnabled="true" />  
  </system.serviceModel>  
 <system.webServer>  
    <modules runAllManagedModulesForAllRequests="true"/>  
  </system.webServer>  
  
</configuration>  
  
```  
  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## Voir aussi  
 [Hébergement dans les services IIS \(Internet Information Services\)](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md)   
 [Instructions relatives à l'hébergement dans les Services Internet \(IIS\)](../../../../docs/framework/wcf/samples/internet-information-service-hosting-instructions.md)   
 [Meilleures pratiques pour l'hébergement dans Internet Information Services](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)   
 [IIS Hosting Using Inline Code](../../../../docs/framework/wcf/samples/iis-hosting-using-inline-code.md)
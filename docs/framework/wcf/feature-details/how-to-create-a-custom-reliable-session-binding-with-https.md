---
title: "Comment&#160;: cr&#233;er une liaison de session fiable personnalis&#233;e &#224; l&#39;aide de HTTPS | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa772232-da1f-4c66-8c94-e36c0584b549
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: cr&#233;er une liaison de session fiable personnalis&#233;e &#224; l&#39;aide de HTTPS
Cette rubrique décrit l'utilisation de la sécurité de transport SSL \(Secure Socket Layer\) avec les sessions fiables.  Pour utiliser une session fiable sur HTTPS, vous devez créer une liaison personnalisée qui utilise une session fiable et le transport HTTPS.  Vous pouvez activer la session fiable soit impérativement en utilisant le code, soit de façon déclarative dans le fichier de configuration.  Cette procédure utilise le client et les fichiers de configuration de service pour activer la session fiable et l'élément [\<httpsTransport\>](../../../../docs/framework/configure-apps/file-schema/wcf/httpstransport.md).  
  
 La partie clé de cette procédure est que l'élément de configuration `endpoint` contient un attribut `bindingConfiguration` qui référence une configuration de liaison personnalisée nommée "reliableSessionOverHttps".  L'élément de configuration [\<liaison\>](../../../../docs/framework/misc/binding.md) peut ensuite référencer ce nom pour spécifier qu'une session fiable et le transport HTTPS sont utilisés en incluant des éléments `reliableSession` et `httpsTransport`.  
  
 Pour la copie source de cet exemple, consultez [Custom Binding Reliable Session over HTTPS](../../../../docs/framework/wcf/samples/custom-binding-reliable-session-over-https.md).  
  
### Pour configurer le service avec une liaison personnalisée afin d'utiliser une session fiable avec HTTPS  
  
1.  Définissez un contrat de service pour le type de service.  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1121)]  
  
2.  Implémentez le contrat de service dans une classe de service.  Notez que l'adresse ou les informations de liaison ne sont pas spécifiées dans l'implémentation du service.  Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[c_HowTo_CreateReliableSessionHTTPS#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/service.cs#1122)]  
  
3.  Créez un fichier Web.config pour configurer un point de terminaison pour `CalculatorService` avec une liaison personnalisée nommée "reliableSessionOverHttps" utilisant une session fiable et le transport HTTPS.  
  
     [!code[c_HowTo_CreateReliableSessionHTTPS#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/web.config#2111)]  
  
4.  Créez un fichier Service.svc qui contient la ligne :  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  Placez le fichier Service.svc dans votre répertoire virtuel IIS \(Internet Information Services\).  
  
### Pour configurer le client avec une liaison personnalisée afin d'utiliser une session fiable avec HTTPS  
  
1.  Utilisez l'outil [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code de métadonnées de service.  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Le client généré contient l'interface `ICalculator` qui définit le contrat de service auquel l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1221)]  
  
3.  L'application cliente générée contient également l'implémentation de `ClientCalculator`.  Notez que les informations d'adresse et de liaison ne sont pas spécifiées n'importe où dans l'implémentation du service.  Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1222)]  
  
4.  Configurez une liaison personnalisée nommée reliableSessionOverHttps pour utiliser le transport HTTPS et des sessions fiables.  
  
     [!code[C_HowTo_CreateReliableSessionHTTPS#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_createreliablesessionhttps/common/app.config#2211)]  
  
5.  Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.  
  
     [!code-csharp[C_HowTo_CreateReliableSessionHTTPS#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_createreliablesessionhttps/cs/client.cs#1223)]  
  
6.  Compilez, puis exécutez le client.  
  
## Exemple  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
## Sécurité .NET Framework  
 Parce que le certificat utilisé dans cet exemple est un certificat de test créé avec Makecert.exe, une alerte de sécurité apparaît lorsque vous essayez d'accéder à une adresse HTTPS, telle que https:\/\/localhost\/servicemodelsamples\/service.svc, depuis votre navigateur.  
  
## Voir aussi  
 [Sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
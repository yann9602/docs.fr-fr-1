---
title: "Comment&#160;: &#233;changer des messages au sein d&#39;une session fiable | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 87cd0e75-dd2c-44c1-8da0-7b494bbdeaea
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: &#233;changer des messages au sein d&#39;une session fiable
Cette rubrique décrit les étapes requises pour activer une session fiable utilisant l'une des liaisons fournies par le système qui prennent en charge une telle session, mais pas par défaut.Vous pouvez activer la session fiable soit de façon impérative en utilisant le code, soit de façon déclarative dans le fichier de configuration.Cette procédure utilise les fichiers de configuration du client et du service pour activer la session fiable et pour stipuler que les messages arrivent dans le même ordre dans lequel ils ont été envoyés.  
  
 La partie clé de cette procédure est que l'élément de configuration de point de terminaison contient un attribut `bindingConfiguration` qui référence une configuration de liaison nommé "Binding1". L'élément de configuration [\<liaison\>](../../../../docs/framework/misc/binding.md) peut référencer ensuite ce nom pour activer des sessions fiables en affectant à l'attribut `enabled` de l'élément [reliableSession](http://msdn.microsoft.com/fr-fr/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b) la valeur `true`.Vous spécifiez les assurances de remise ordonnée pour la session fiable en affectant à l'attribut `ordered` la valeur `true`.  
  
 Pour la copie source de cet exemple, consultez [WS Reliable Session](../../../../docs/framework/wcf/samples/ws-reliable-session.md).  
  
### Pour configurer le service avec une liaison WSHttpBinding afin d'utiliser une session fiable  
  
1.  Définissez un contrat de service pour le type de service.  
  
     [!code-csharp[c_HowTo_UseReliableSession#1121](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1121)]  
  
2.  Implémentez le contrat de service dans une classe de service.Notez que l'adresse ou les informations de liaison ne sont pas spécifiées dans l'implémentation du service.Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[c_HowTo_UseReliableSession#1122](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/service.cs#1122)]  
  
3.  Créez un fichier Web.config pour configurer un point de terminaison pour `CalculatorService` qui utilise <xref:System.ServiceModel.WSHttpBinding> avec la session fiable activée et la remise ordonnée des messages requise.  
  
     [!code[c_HowTo_UseReliableSession#2111](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/web.config#2111)]  
  
4.  Créez un fichier Service.svc qui contient la ligne :  
  
    ```  
    <%@ServiceHost language=c# Service="CalculatorService" %>   
    ```  
  
5.  Placez le fichier Service.svc dans votre répertoire virtuel IIS \(Internet Information Services\).  
  
### Pour configurer le client avec une liaison WSHttpBinding afin d'utiliser une session fiable  
  
1.  Utilisez [Outil Service Model Metadata Tool \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) à partir de la ligne de commande pour générer le code à partir des métadonnées du service :  
  
    ```  
    Svcutil.exe <service's Metadata Exchange (MEX) address or HTTP GET address>   
    ```  
  
2.  Le client généré contient l'interface `ICalculator` qui définit le contrat de service que l'implémentation du client doit satisfaire.  
  
     [!code-csharp[C_HowTo_UseReliableSession#1221](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1221)]  
  
3.  L'application cliente générée contient également l'implémentation de `ClientCalculator`.Notez que les informations d'adresse et de liaison ne sont pas spécifiées n'importe où dans l'implémentation du service.Par ailleurs, il n'est pas nécessaire d'écrire du code pour récupérer ces informations à partir du fichier de configuration.  
  
     [!code-csharp[C_HowTo_UseReliableSession#1222](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1222)]  
  
4.  Svcutil.exe génère également la configuration du client qui utilise la classe <xref:System.ServiceModel.WSHttpBinding>.Ce fichier doit être nommé dans le fichier App.config lors de l'utilisation de [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].  
  
     [!code[C_HowTo_UseReliableSession#2211](../../../../samples/snippets/common/VS_Snippets_CFX/c_howto_usereliablesession/common/app.config#2211)]  
  
5.  Créez une instance `ClientCalculator` dans une application, puis appelez les opérations de service.  
  
     [!code-csharp[C_HowTo_UseReliableSession#1223](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_usereliablesession/cs/client.cs#1223)]  
  
6.  Compilez, puis exécutez le client.  
  
## Exemple  
<!-- TODO: review snippet reference  [!CODE [Microsoft.Win32.RegistryKey#4](Microsoft.Win32.RegistryKey#4)]  -->  
  
 Plusieurs liaisons fournies par le système prennent en charge des sessions fiables par défaut.Elles incluent :  
  
-   <xref:System.ServiceModel.WSDualHttpBinding>  
  
-   <xref:System.ServiceModel.NetNamedPipeBinding>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>  
  
 Pour un exemple de création d'une liaison personnalisée prenant en charge les sessions fiables, consultez [Comment : créer une liaison de session fiable personnalisée à l'aide de HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).  
  
## Voir aussi  
 [Sessions fiables](../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
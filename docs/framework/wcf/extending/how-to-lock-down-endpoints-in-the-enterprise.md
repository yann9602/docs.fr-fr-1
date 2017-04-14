---
title: "Comment&#160;: verrouiller des points de terminaison dans l&#39;entreprise | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1b7eaab7-da60-4cf7-9d6a-ec02709cf75d
caps.latest.revision: 21
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 21
---
# Comment&#160;: verrouiller des points de terminaison dans l&#39;entreprise
Les entreprises de grande taille exigent souvent que les applications soient développées conformément à leurs stratégies de sécurité.  La rubrique suivante explique comment développer et installer un validateur de point de terminaison client permettant de valider l'ensemble des applications clientes [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] installées sur les ordinateurs.  
  
 Dans ce cas, il s'agit d'un validateur client, car ce comportement de point de terminaison est ajouté à la section [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) du client dans le fichier machine.config.  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] charge uniquement les comportements de point de terminaison communs pour les applications clientes et uniquement les comportements de service communs pour les applications de service.  Pour installer ce même validateur pour les applications de service, le validateur doit être un comportement de service.  [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] consultez la section [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md).  
  
> [!IMPORTANT]
>  Les comportements de service ou de point de terminaison non marqués avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> \(APTCA\) qui sont ajoutés à la section [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) d'un fichier de configuration ne sont pas exécutés lorsque l'application s'exécute dans un environnement de confiance partielle, et aucune exception n'est levée lorsque cela se produit.  Pour appliquer l'exécution des comportements courants tels que les validateurs, vous devez effectuer l'une des actions suivantes :  
>   
>  \-\- Marquez votre comportement courant avec l'attribut <xref:System.Security.AllowPartiallyTrustedCallersAttribute> afin qu'il soit exécuté lorsqu'il est déployé comme une application de confiance partielle.  Notez qu'une entrée de Registre peut être définie sur l'ordinateur pour interdire l'exécution des assemblys marqués avec l'attribut APTCA.  
>   
>  \-\- Si l'application est déployée comme une application de confiance partielle, vérifiez que les utilisateurs ne peuvent pas modifier les paramètres de sécurité d'accès du code pour exécuter l'application dans un environnement de confiance partielle.  S'ils peuvent le faire, le validateur personnalisé ne s'exécute pas et aucune exception n'est levée.  Pour savoir comment garantir cette configuration, consultez l'option `levelfinal` à l'aide de l'[outil Stratégie de sécurité d'accès du code \(Caspol.exe\)](http://go.microsoft.com/fwlink/?LinkId=248222).  
>   
>  Pour plus d'informations, consultez [Meilleures pratiques dans un environnement de confiance partielle](../../../../docs/framework/wcf/feature-details/partial-trust-best-practices.md) et [Scénarios de déploiement pris en charge](../../../../docs/framework/wcf/feature-details/supported-deployment-scenarios.md).  
  
### Pour créer le validateur de point de terminaison  
  
1.  Créez un objet <xref:System.ServiceModel.Description.IEndpointBehavior> avec les étapes de validation souhaitées dans la méthode <xref:System.ServiceModel.Description.IEndpointBehavior.Validate%2A>.  Le code suivant fournit un exemple.  \(`InternetClientValidatorBehavior` est extrait de l'exemple [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md).\)  
  
     [!code-csharp[LockdownValidation#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorbehavior.cs#2)]  
  
2.  Créez un objet <xref:System.ServiceModel.Configuration.BehaviorExtensionElement> qui enregistre le validateur de point de terminaison créé à l'étape 1.  L'exemple de code suivant illustre ce point.  \(Le code d'origine pour cet exemple se trouve dans l'exemple [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md).\)  
  
     [!code-csharp[LockdownValidation#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/internetclientvalidatorelement.cs#3)]  
  
3.  Assurez\-vous que l'assembly compilé est signé avec un nom fort.  Pour plus d'informations, consultez [Outil Strong Name Tool \(SN.EXE\)](http://go.microsoft.com/fwlink/?LinkId=248217) et les commandes du compilateur pour votre langage.  
  
### Pour installer le validateur dans l'ordinateur cible  
  
1.  Installez le validateur de point de terminaison à l'aide du mécanisme approprié.  Dans une entreprise, cela peut s'effectuer en utilisant la stratégie de groupe ou SMS \(Systems Management Server\).  
  
2.  Installez l'assembly avec nom fort dans le Global Assembly Cache à l'aide de l'[outil Global Assembly Cache \(Gacutil.exe\)](http://msdn.microsoft.com/library/ex0ss12c\(v=vs.110\).aspx).  
  
3.  Utilisez les types d'espaces de noms <xref:System.Configuration?displayProperty=fullName> pour :  
  
    1.  Ajoutez l'extension à la section [\<behaviorExtensions\>](../../../../docs/framework/configure-apps/file-schema/wcf/behaviorextensions.md) à l'aide d'un nom de type complet et verrouillez l'élément.  
  
         [!code-csharp[LockdownValidation#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#5)]  
  
    2.  Ajoutez l'élément de comportement à la propriété `EndpointBehaviors` de la section [\<commonBehaviors\>](../../../../docs/framework/configure-apps/file-schema/wcf/commonbehaviors.md) et verrouillez l'élément.  \(Pour installer le validateur sur le service, le validateur doit être un <xref:System.ServiceModel.Description.IServiceBehavior> et être ajouté à la propriété `ServiceBehaviors`.\) L'exemple de code suivant illustre la configuration appropriée après les étapes a.  et b., à la seule exception qu'il n'y a pas de nom fort.  
  
         [!code-csharp[LockdownValidation#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#6)]  
  
    3.  Enregistrez le fichier machine.config.  L'exemple de code suivant exécute l'ensemble des tâches dans l'étape 3, mais enregistre une copie du fichier machine.config modifié localement.  
  
         [!code-csharp[LockdownValidation#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#7)]  
  
## Exemple  
 L'exemple de code suivant indique comment ajouter un comportement commun au fichier machine.config et enregistrer une copie sur le disque.  `InternetClientValidatorBehavior` est extrait de l'exemple [Security Validation](../../../../docs/framework/wcf/samples/security-validation.md).  
  
 [!code-csharp[LockdownValidation#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/lockdownvalidation/cs/hostapplication.cs#1)]  
  
## Sécurité .NET Framework  
 Vous pouvez également chiffrer les éléments du fichier de configuration.  Pour plus d'informations, consultez la section Voir aussi.  
  
## Voir aussi  
 [Chiffrement des éléments de fichier de configuration à l'aide de DPAPI](http://go.microsoft.com/fwlink/?LinkId=94954)   
 [Chiffrement des éléments de fichier de configuration à l'aide de RSA](http://go.microsoft.com/fwlink/?LinkId=94955)
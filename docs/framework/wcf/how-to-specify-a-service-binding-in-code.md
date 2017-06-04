---
title: "Comment&#160;: sp&#233;cifier une liaison de service dans le code | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 67ab5dd8-79c1-4e62-aa75-828ea918a53a
caps.latest.revision: 9
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 9
---
# Comment&#160;: sp&#233;cifier une liaison de service dans le code
Dans cet exemple, un contrat `ICalculator` est défini pour un service de calculatrice, le service est implémenté dans la classe `CalculatorService`, puis son point de terminaison est défini dans du code, où il est spécifié que le service doit utiliser la classe <xref:System.ServiceModel.BasicHttpBinding>.  
  
 Il est généralement conseillé de spécifier de façon déclarative les informations de liaison et d'adresse dans la configuration plutôt que de manière impérative dans le code.La définition de points de terminaison dans le code est généralement peu pratique car les liaisons et les adresses pour un service déployé sont en général différentes de celles utilisées au cours du développement du service.Plus généralement, le fait de laisser les informations de liaison et d'adressage hors du code leur permet de changer sans avoir à recompiler ou à redéployer l'application.  
  
 Pour une description de la manière de configurer ce service à l'aide des éléments de configuration au lieu de code, consultez [Comment : spécifier une liaison de service dans la configuration](../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
### Pour spécifier l'utilisation de BasicHttpBinding dans du code pour le service  
  
1.  Définissez un contrat de service pour le type de service.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#1)]
     [!code-vb[C_HowTo_CodeServiceBinding#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#1)]  
  
2.  Implémentez le contrat de service dans une classe de service.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#2)]
     [!code-vb[C_HowTo_CodeServiceBinding#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#2)]  
  
3.  Dans l'application d'hébergement, créez l'adresse de base pour le service et la liaison à utiliser avec le service.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#3)]
     [!code-vb[C_HowTo_CodeServiceBinding#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#3)]  
  
4.  Créez l'hôte pour le service, ajoutez le point de terminaison, puis ouvrez l'hôte.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#4)]
     [!code-vb[C_HowTo_CodeServiceBinding#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#4)]  
  
### Pour modifier les valeurs par défaut des propriétés de liaison  
  
1.  Pour modifier l'une des valeurs de propriété par défaut de la classe <xref:System.ServiceModel.BasicHttpBinding>, affectez la nouvelle valeur de propriété sur la liaison avant de créer l'hôte.Par exemple, pour modifier les valeurs par défaut de délai d'attente d'ouverture et de fermeture de 1 minute à 2 minutes, procédez comme suit.  
  
     [!code-csharp[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_howto_codeservicebinding/cs/source.cs#5)]
     [!code-vb[C_HowTo_CodeServiceBinding#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_howto_codeservicebinding/vb/source.vb#5)]  
  
## Voir aussi  
 [Utilisation de liaisons pour configurer des services et des clients](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)   
 [Spécification d'une adresse de point de terminaison](../../../docs/framework/wcf/specifying-an-endpoint-address.md)
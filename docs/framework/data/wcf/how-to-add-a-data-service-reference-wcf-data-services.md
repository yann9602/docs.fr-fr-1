---
title: "Proc&#233;dure&#160;: ajouter une r&#233;f&#233;rence de service de donn&#233;es (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Services de données WCF, configuration"
ms.assetid: 62c6f318-3ee1-433a-b7a3-efa234c3034c
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: ajouter une r&#233;f&#233;rence de service de donn&#233;es (WCF Data Services)
Vous pouvez utiliser la boîte de dialogue **Ajouter une référence de service** dans Visual Studio pour ajouter une référence à [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)].  De cette manière, vous pouvez accéder plus facilement à un service de données dans une application cliente que vous développez dans Visual Studio.  Lorsque vous complétez cette procédure, les classes de données sont générées selon les métadonnées obtenues auprès du service de données.  Pour plus d'informations, consultez [Génération de la bibliothèque cliente du service de données](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md).  
  
### Pour ajouter une référence de service de données  
  
1.  \(Facultatif\) Si le service de données n'appartient pas à la solution et n'est pas déjà en cours d'exécution, démarrez le service de données et notez l'URI du service de données.  
  
2.  Cliquez avec le bouton droit sur le projet client, puis sélectionnez **Ajouter une référence de service**.  
  
3.  Si le service de données fait partie de la solution actuelle, cliquez sur **Découvrir**.  
  
     ou  
  
     Dans la zone de texte **Adresse**, tapez l'URL de base du service de données, telle que `http://localhost:1234/Northwind.svc`, puis cliquez sur **OK**.  
  
4.  Cliquez sur **OK**.  
  
     Cette opération ajoute un nouveau fichier de code qui contient les classes de données utilisées pour accéder et interagir avec les ressources du service des données sous la forme d'objets.  
  
## Voir aussi  
 [Démarrage rapide](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)
---
title: "Usage of Serialization Binder | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ab46c087-200c-45bf-9c95-5a6cda6e8b98
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# Usage of Serialization Binder
Cet exemple montre comment utiliser le <xref:System.Runtime.Serialization.SerializationBinder> pour modifier la version d'un type générique lorsqu'il est sérialisé.  
  
## Démonstrations  
 <xref:System.Runtime.Serialization.SerializationBinder>, <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>  
  
## Discussion  
 Cet exemple montre comment deux entités qui ciblent des versions différentes du [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] peuvent communiquer à l'aide du formateur binary et du binder de sérialisation.  
  
 Le développement de cet exemple a été réalisé à l'aide de .NET Remoting.L'exemple se compose d'un serveur ciblant [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], qui implémente un contrat avec les types génériques, et deux clients différents, l'un ciblant [!INCLUDE[dnprdnlong](../../../../includes/dnprdnlong-md.md)] et l'autre ciblant [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)].  
  
 Le serveur attache un <xref:System.Runtime.Serialization.SerializationBinder> au formateur binary pour être en mesure de modifier la version des types en conséquence lors de la sérialisation, si les deux clients peuvent désérialiser correctement ces types.  
  
#### Pour configurer, générer et exécuter l'exemple  
  
1.  Pour exécuter le client, cliquez avec le bouton droit sur la solution, SBGenericsVTS \(6 projets\), puis sélectionnez **Propriétés**.  
  
2.  Dans **Propriétés communes**, sélectionnez **Projet de démarrage**, puis **Plusieurs projets de démarrage**.  
  
3.  Sélectionnez d'abord **Server**, puis **Client20**, puis **Client40**.Sélectionnez l'action **Démarrer** pour ces trois projets et gardez la valeur **Aucune** pour le reste.  
  
4.  Cliquez sur **OK** et appuyez sur F5 pour exécuter l'exemple.
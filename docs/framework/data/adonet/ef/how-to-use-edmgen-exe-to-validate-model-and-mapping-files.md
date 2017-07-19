---
title: "Proc&#233;dure&#160;: utiliser EdmGen.exe pour valider les fichiers de mod&#232;le et de mappage (Entity&#160;Framework) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
  - "jsharp"
ms.assetid: 2641906a-971a-4d0b-8aee-13fabc02a1cc
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Proc&#233;dure&#160;: utiliser EdmGen.exe pour valider les fichiers de mod&#232;le et de mappage (Entity&#160;Framework)
Cette rubrique montre comment utiliser l'outil [EDM Generator \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md) pour valider les fichiers de modèle et de mappage.  Pour plus d'informations, consultez [Entity Data Model](../../../../../docs/framework/data/adonet/entity-data-model.md).  
  
### Pour valider le modèle School à l'aide d'EdmGen.exe  
  
1.  Créez la base de données School.  Pour plus d'informations, consultez [Creating the School Sample Database](http://msdn.microsoft.com/fr-fr/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  Générez le modèle School.  Pour plus d'informations, consultez [Procédure : utiliser EdmGen.exe pour générer les fichiers de modèle et de mappage \(Entity Framework\)](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-the-model-and-mapping-files.md).  
  
3.  À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```scr  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:ValidateArtifacts /inssdl:.\School.ssdl /inmsl:.\School.msl /incsdl:.\School.csdl  
    ```  
  
## Voir aussi  
 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/fr-fr/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/fr-fr/91076853-0881-421b-837a-f582f36be527)   
 [How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/fr-fr/b18a9d16-e10b-4043-ba91-b632f85a2579)   
 [Procédure : utiliser EdmGen.exe pour générer le code de couche objet](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-generate-object-layer-code.md)
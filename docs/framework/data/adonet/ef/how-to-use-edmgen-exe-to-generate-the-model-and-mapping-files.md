---
title: "Proc&#233;dure&#160;: utiliser EdmGen.exe pour g&#233;n&#233;rer les fichiers de mod&#232;le et de mappage (Entity&#160;Framework) | Microsoft Docs"
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
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: 4
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 4
---
# Proc&#233;dure&#160;: utiliser EdmGen.exe pour g&#233;n&#233;rer les fichiers de mod&#232;le et de mappage (Entity&#160;Framework)
Cette rubrique montre comment utiliser l'outil EDM Generator \(EdmGen.exe\) pour générer les fichiers suivants à partir de la base de données School :  
  
-   un modèle conceptuel \(fichier .csdl\) ;  
  
-   un modèle de stockage \(fichier .ssdl\) ;  
  
-   un mappage entre les modèles conceptuel et de stockage \(fichier .msl\) ;  
  
-   du code de couche objet en Visual Basic ou C\# ;  
  
-   des fichiers de vue.  
  
 L'outil EdmGen.exe utilise la commande \/mode:FullGeneration pour générer les fichiers répertoriés ci\-dessus.  Pour plus d'informations sur les commandes EdmGen.exe, consultez [EDM Generator \(EdmGen.exe\)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 L'utilisation d'EdmGen.exe pour générer les fichiers de modèle et de mappage ne vous dispense pas de configurer votre projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pour qu'il utilise [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)].  Pour plus d'informations, consultez [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/fr-fr/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Un modèle conceptuel généré par EdmGen.exe comprend tous les objets de la base de données.  Si vous souhaitez générer un modèle conceptuel qui ne comporte que des objets spécifiques, utilisez l'Assistant EDM.  Pour plus d'informations, consultez [How to: Use the Entity Data Model Wizard](http://msdn.microsoft.com/fr-fr/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet Visual Basic  
  
1.  Créez la base de données School.  Pour plus d'informations, consultez [Creating the School Sample Database](http://msdn.microsoft.com/fr-fr/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
  
    ```  
  
### Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet C\#  
  
1.  Créez la base de données School.  Pour plus d'informations, consultez [Creating the School Sample Database](http://msdn.microsoft.com/fr-fr/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## Voir aussi  
 [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)   
 [How to: Manually Configure an Entity Framework Project](http://msdn.microsoft.com/fr-fr/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)   
 [How to: Pre\-Generate Views to Improve Query Performance](http://msdn.microsoft.com/fr-fr/b18a9d16-e10b-4043-ba91-b632f85a2579)   
 [ADO.NET Entity Data Model  Tools](http://msdn.microsoft.com/fr-fr/91076853-0881-421b-837a-f582f36be527)   
 [Procédure : utiliser EdmGen.exe pour valider les fichiers de modèle et de mappage \(Entity Framework\)](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)
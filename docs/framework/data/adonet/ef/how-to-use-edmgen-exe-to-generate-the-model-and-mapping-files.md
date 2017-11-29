---
title: "Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et les fichiers de mappage"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 40db462d-2fd2-4cc1-ad86-d280403e63fa
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 741da2e7f69d5f8fa54f07046d88fec9cf722dbf
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-edmgenexe-to-generate-the-model-and-mapping-files"></a>Comment : utiliser EdmGen.exe pour générer les fichiers de modèle et les fichiers de mappage
Cette rubrique montre comment utiliser l'outil EDM Generator (EdmGen.exe) pour générer les fichiers suivants à partir de la base de données School :  
  
-   un modèle conceptuel (fichier .csdl) ;  
  
-   un modèle de stockage (fichier .ssdl) ;  
  
-   un mappage entre les modèles conceptuel et de stockage (fichier .msl) ;  
  
-   du code de couche objet en Visual Basic ou C# ;  
  
-   des fichiers de vue.  
  
 L'outil EdmGen.exe utilise la commande /mode:FullGeneration pour générer les fichiers répertoriés ci-dessus. Pour plus d’informations sur les commandes d’EdmGen.exe, consultez [EDM Generator (EdmGen.exe)](../../../../../docs/framework/data/adonet/ef/edm-generator-edmgen-exe.md).  
  
 L'utilisation d'EdmGen.exe pour générer les fichiers de modèle et de mappage ne vous dispense pas de configurer votre projet [!INCLUDE[vsprvs](../../../../../includes/vsprvs-md.md)] pour qu'il utilise [!INCLUDE[adonet_ef](../../../../../includes/adonet-ef-md.md)]. Pour plus d’informations, consultez [Comment : configurer manuellement un projet Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e).  
  
> [!NOTE]
>  Un modèle conceptuel généré par EdmGen.exe comprend tous les objets de la base de données. Si vous souhaitez générer un modèle conceptuel qui ne comporte que des objets spécifiques, utilisez l'Assistant EDM. Pour plus d’informations, consultez [Comment : utiliser l’Assistant Entity Data Model](http://msdn.microsoft.com/en-us/dadb058a-c5d9-4c5c-8b01-28044112231d).  
  
### <a name="to-generate-the-school-model-for-a-visual-basic-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet Visual Basic  
  
1.  Créez la base de données School. Pour plus d’informations, consultez [création de la base de données School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:VB  
    ```  
  
### <a name="to-generate-the-school-model-for-a-c-project-using-edmgenexe"></a>Pour générer à l'aide de l'outil EdmGen.exe le modèle School pour un projet C#  
  
1.  Créez la base de données School. Pour plus d’informations, consultez [création de la base de données School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0).  
  
2.  À l'invite de commandes, exécutez la commande suivante sans saut de ligne :  
  
    ```  
    "%windir%\Microsoft.NET\Framework\v4.0.30319\edmgen.exe" /mode:fullgeneration   
    /c:"Data Source=%datasourceserver%; Initial Catalog=School; Integrated Security=SSPI"   
    /project:School /entitycontainer:SchoolEntities /namespace:SchoolModel /language:CSharp  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 [Modélisation et mappage](../../../../../docs/framework/data/adonet/ef/modeling-and-mapping.md)  
 [Comment : configurer manuellement un projet Entity Framework](http://msdn.microsoft.com/en-us/73f6ae1d-b3b2-4577-aebd-ad5a75954e9e)  
 [Comment : prégénérer des vues pour améliorer les performances des requêtes](http://msdn.microsoft.com/en-us/b18a9d16-e10b-4043-ba91-b632f85a2579)  
 [Outils ADO.NET Entity Data Model](http://msdn.microsoft.com/en-us/91076853-0881-421b-837a-f582f36be527)  
 [Comment : utiliser EdmGen.exe pour valider les fichiers de mappage et de modèle](../../../../../docs/framework/data/adonet/ef/how-to-use-edmgen-exe-to-validate-model-and-mapping-files.md)

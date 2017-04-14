---
title: "Proc&#233;dure&#160;: cr&#233;er un projet LINQ to DataSet dans Visual Studio | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# Proc&#233;dure&#160;: cr&#233;er un projet LINQ to DataSet dans Visual Studio
Les différents types de projets [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] nécessitent certains espaces de noms importés \(Visual Basic\) ou directives `using` \(C\#\) et références.  Il doit y avoir au minimum une référence à System.Core.dll et une directive `using` pour <xref:System.Linq>.  Celles\-ci sont fournies par défaut si vous créez un projet [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)].  [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requiert également une référence à System.Data.dll et System.Data.DataSetExtensions.dll et une directive `Imports` \(Visual Basic\) ou `using` \(C\#\).  
  
 Si vous effectuez la mise à niveau d'un projet à partir d'une version antérieure de Visual Studio, vous devrez fournir manuellement ces références liées à LINQ.  Il vous faudra également définir manuellement le projet pour cibler le .NET Framework version 3.5.  
  
> [!NOTE]
>  Si vous effectuez une génération à partir d'une invite de commandes, vous devez référencer manuellement les DLL liées à LINQ dans `drive`**:**\\Program Files\\Reference Assemblies\\Microsoft\\Framework\\v3.5.  
  
### Pour cibler .NET Framework 3.5  
  
1.  Dans [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], créez un nouveau projet Visual Basic ou C\#. Vous pouvez également ouvrir un projet Visual Basic ou C\# qui a été créé dans Visual Studio 2005 et suivre les invites pour le convertir en projet [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Pour un projet C\#, cliquez sur le menu **Projet**, puis sur **Propriétés**.  
  
    1.  Dans la page de propriétés **Application**, sélectionnez .NET Framework 3.5 dans la liste déroulante **Infrastructure cible**.  
  
3.  Pour un projet Visual Basic, cliquez sur le menu **Projet**, puis cliquez sur **Propriétés**.  
  
    1.  Dans la page de propriétés **Compiler**, cliquez sur **Options avancées de compilation**, puis sélectionnez .NET Framework 3.5 dans la liste déroulante **Infrastructure cible \(toutes les configurations\)**.  
  
4.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**, cliquez sur l'onglet **.NET**, faites défiler jusqu'à **System.Core**, cliquez dessus, puis cliquez sur **OK**.  
  
5.  Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Linq> à votre fichier de code source ou votre projet.  
  
     Pour plus d'informations, consultez [using, directive](../Topic/using%20Directive%20\(C%23%20Reference\).md) ou [Comment : ajouter ou supprimer des espaces de noms importés \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md).  
  
### Pour activer les fonctionnalités LINQ to DataSet  
  
1.  Si nécessaire, suivez les étapes décrites précédemment dans cette rubrique pour ajouter une référence à System.Core.dll et une directive `using` ou un espace de noms importé pour System.Linq.  
  
2.  Dans un projet C\# ou Visual Basic, cliquez sur le menu **Projet**, puis cliquez sur **Ajouter une référence**.  
  
3.  Dans la boîte de dialogue **Ajouter une référence**, cliquez sur l'onglet **.NET** s'il n'est pas au premier plan.  Faites défiler vers le bas jusqu'à **System.Data** et **System.Data.DataSetExtensions**, puis cliquez dessus.  Cliquez sur **OK**.  
  
4.  Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Data> à votre fichier de code source ou votre projet.  Pour plus d'informations, consultez [using, directive](../Topic/using%20Directive%20\(C%23%20Reference\).md) ou [Comment : ajouter ou supprimer des espaces de noms importés \(Visual Basic\)](../Topic/How%20to:%20Add%20or%20Remove%20Imported%20Namespaces%20\(Visual%20Basic\).md).  
  
5.  Ajouter une référence à System.Data.DataSetExtensions.dll pour la fonctionnalité LINQ to Dataset.  Ajoutez une référence à System.Data.dll si elle n'existe pas déjà.  
  
6.  Si vous le souhaitez, ajoutez une directive `using` ou un espace de noms importé pour `System.Data.Common` ou `System.Data.SqlClient`, selon la façon dont vous vous connectez à la base de données.  
  
## Voir aussi  
 [Mise en route](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)   
 [Getting Started with LINQ](http://msdn.microsoft.com/fr-fr/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)
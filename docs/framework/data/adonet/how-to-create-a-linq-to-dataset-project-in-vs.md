---
title: "Comment : créer un projet LINQ to DataSet dans Visual Studio"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 49ba6cb0-cdd2-4571-aeaa-25bf0f40e9b3
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c749cdd56f0c964b84788b05470406234ef3eb0a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-linq-to-dataset-project-in-visual-studio"></a>Comment : créer un projet LINQ to DataSet dans Visual Studio
Les différents types de projets [!INCLUDE[vbteclinq](../../../../includes/vbteclinq-md.md)] nécessitent certains espaces de noms importés (Visual Basic) ou directives `using` (C#) et références. Il doit y avoir au minimum une référence à System.Core.dll et une directive `using` pour <xref:System.Linq>. Celles-ci sont fournies par défaut si vous créez un projet [!INCLUDE[csharp_orcas_long](../../../../includes/csharp-orcas-long-md.md)]. [!INCLUDE[linq_dataset](../../../../includes/linq-dataset-md.md)] requiert également une référence à System.Data.dll et System.Data.DataSetExtensions.dll et une directive `Imports` (Visual Basic) ou `using` (C#).  
  
 Si vous effectuez la mise à niveau d'un projet à partir d'une version antérieure de Visual Studio, vous devrez fournir manuellement ces références liées à LINQ. Il vous faudra également définir manuellement le projet pour cibler le .NET Framework version 3.5.  
  
> [!NOTE]
>  Si vous générez à partir d’une invite de commandes, vous devez référencer manuellement les DLL liées à LINQ dans `drive` **:**\Program Assemblies\Microsoft\Framework\v3.5.  
  
### <a name="to-target-the-net-framework-35"></a>Pour cibler .NET Framework 3.5  
  
1.  Dans [!INCLUDE[vs_orcas_long](../../../../includes/vs-orcas-long-md.md)], créez un nouveau projet Visual Basic ou C#. Vous pouvez également ouvrir un projet Visual Basic ou C# qui a été créé dans Visual Studio 2005 et suivre les invites pour le convertir en projet [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
2.  Pour un projet c#, cliquez sur le **projet** menu, puis sur **propriétés**.  
  
    1.  Dans le **Application** page de propriétés, sélectionnez .NET Framework 3.5 dans le **Framework cible** liste déroulante.  
  
3.  Pour un projet Visual Basic, cliquez sur le **projet** menu, puis sur **propriétés**.  
  
    1.  Dans le **compiler** page de propriétés, cliquez sur **Options avancées de compilation** , puis sélectionnez .NET Framework 3.5 dans le **Framework cible (toutes les configurations)** liste déroulante.  
  
4.  Sur le **projet** menu, cliquez sur **ajouter une référence**, cliquez sur le **.NET** onglet, faites défiler jusqu'à **System.Core**, cliquez dessus, puis cliquez sur  **OK**.  
  
5.  Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Linq> à votre fichier de code source ou votre projet.  
  
     Pour plus d’informations, consultez [à l’aide de la Directive](~/docs/csharp/language-reference/keywords/using-directive.md) ou [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
### <a name="to-enable-linq-to-dataset-functionality"></a>Pour activer les fonctionnalités LINQ to DataSet  
  
1.  Si nécessaire, suivez les étapes décrites précédemment dans cette rubrique pour ajouter une référence à System.Core.dll et une directive `using` ou un espace de noms importé pour System.Linq.  
  
2.  En c# ou Visual Basic, cliquez sur le **projet** menu, puis sur **ajouter une référence**.  
  
3.  Dans le **ajouter une référence** boîte de dialogue, cliquez sur le **.NET** onglet si elle n’est pas visible. Faites défiler jusqu'à **System.Data** et **System.Data.DataSetExtensions** et cliquez dessus. Cliquez sur le **OK** bouton.  
  
4.  Ajoutez une directive `using` ou un espace de noms importé pour <xref:System.Data> à votre fichier de code source ou votre projet. Pour plus d’informations, consultez [à l’aide de la Directive](~/docs/csharp/language-reference/keywords/using-directive.md) ou [Comment : ajouter ou supprimer des espaces de noms importés (Visual Basic)](/visualstudio/ide/how-to-add-or-remove-imported-namespaces-visual-basic).  
  
5.  Ajouter une référence à System.Data.DataSetExtensions.dll pour la fonctionnalité LINQ to Dataset. Ajoutez une référence à System.Data.dll si elle n'existe pas déjà.  
  
6.  Si vous le souhaitez, ajoutez une directive `using` ou un espace de noms importé pour `System.Data.Common` ou `System.Data.SqlClient`, selon la façon dont vous vous connectez à la base de données.  
  
## <a name="see-also"></a>Voir aussi  
 [Prise en main](../../../../docs/framework/data/adonet/getting-started-linq-to-dataset.md)  
 [Bien démarrer avec LINQ](http://msdn.microsoft.com/library/6cc9af04-950a-4cc3-83d4-2aeb4abe4de9)

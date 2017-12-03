---
title: "Écriture de projets ciblant le .NET Framework versions 3.0 et 3.5 dans Visual Studio 2010"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6dc6657bad5cc11eaa723c733319673468749b79
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2017
---
# <a name="writing-projects-targeting-the-net-framework-30-and-35-in-visual-studio-2010"></a>Écriture de projets ciblant le .NET Framework versions 3.0 et 3.5 dans Visual Studio 2010
Vous pouvez utiliser [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] pour créer des projets qui ciblent le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 ou 3.5. Cette rubrique décrit comment procéder.  
  
> [!NOTE]
>  Lorsque vous ajoutez des activités, assurez-vous que la version souhaitée du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] est définie. La modification de la version cible du workflow après que les activités ont été ajoutées entraînera l'échec de la validation du workflow.  
  
> [!WARNING]
>  L'ouverture de workflows existants dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] qui ont des activités .Net Framework 3.5 provoquera une erreur au niveau de `this.SetValue()`. Pour ouvrir les projets créés dans les versions antérieures du .NET Framework, ouvrez d'abord un workflow vide dans le concepteur, puis ajoutez une activité .NET Framework 3.5.  
  
## <a name="to-create-a-net-framework--30-or-35-project-with-visual-studio-2010"></a>Pour créer un projet .NET Framework 3.0 ou 3.5 avec Visual Studio 2010  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **fichier**, **nouveau**, **projet**.  
  
3.  Dans la liste déroulante en haut de la boîte de dialogue, sélectionnez la version souhaitée du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## <a name="to-upgrade-the-targeted-version-of-the-net-framework"></a>Pour mettre à niveau la version ciblée du .NET Framework  
  
1.  Cliquez sur le projet dans l’Explorateur de solutions, puis sélectionnez **propriétés**.  
  
2.  Dans le **Framework cible** liste déroulante, sélectionnez la version souhaitée.

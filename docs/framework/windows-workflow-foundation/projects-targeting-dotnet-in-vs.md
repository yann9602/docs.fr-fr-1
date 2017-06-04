---
title: "&#201;criture de projets ciblant le .NET Framework versions&#160;3.0 et 3.5 dans Visual Studio&#160;2010 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 81858ab7-763c-4eac-83fe-d7205e5c4c98
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &#201;criture de projets ciblant le .NET Framework versions&#160;3.0 et 3.5 dans Visual Studio&#160;2010
Vous pouvez utiliser [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] pour créer des projets qui ciblent le [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] version 3.0 ou 3.5.Cette rubrique décrit comment procéder.  
  
> [!NOTE]
>  Lorsque vous ajoutez des activités, assurez\-vous que la version souhaitée du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] est définie.La modification de la version cible du workflow après que les activités ont été ajoutées entraînera l'échec de la validation du workflow.  
  
> [!WARNING]
>  L'ouverture de workflows existants dans [!INCLUDE[vs2010](../../../includes/vs2010-md.md)] qui ont des activités .Net Framework 3.5 provoquera une erreur au niveau de `this.SetValue()`.Pour ouvrir les projets créés dans les versions antérieures du .NET Framework, ouvrez d'abord un workflow vide dans le concepteur, puis ajoutez une activité .NET Framework 3.5.  
  
## Pour créer un projet .NET Framework 3.0 ou 3.5 avec Visual Studio 2010  
  
1.  Ouvrez [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].  
  
2.  Sélectionnez **Fichier**, **Nouveau**, puis **Projet**.  
  
3.  Dans la liste déroulante en haut de la boîte de dialogue, sélectionnez la version souhaitée du [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
## Pour mettre à niveau la version ciblée du .NET Framework  
  
1.  Cliquez avec le bouton droit sur le projet dans l'Explorateur de solutions, puis sélectionnez **Propriétés**.  
  
2.  Dans la liste déroulante **Framework cible**, sélectionnez la version souhaitée.
---
title: "Localisation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "développement d'applications (.NET Framework), localisation"
  - "blocs de code"
  - "culture, localisation"
  - "applications globales, localisation"
  - "globalisation (.NET Framework), localisation"
  - "applications internationales (.NET Framework), localisation"
  - "localisation (.NET Framework), à propos de la localisation"
  - "localiser des ressources"
  - "blocs d'interface utilisateur"
  - "applications universelles, localisation"
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: 8
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 8
---
# Localisation
La localisation est le processus consistant à traduire les ressources d'une application afin d'obtenir des versions localisées pour chaque culture que l'application prendra en charge.  Vous ne devez aborder l'étape de localisation qu'après avoir vérifié, lors de l'étape [Révision de l'adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md), que l'application globalisée est prête pour la localisation.  
  
 Une application qui est prête pour la localisation est divisée en deux blocs conceptuels, le premier contenant tous les éléments de l'interface utilisateur et le second le code exécutable.  Le bloc d'interface utilisateur contient uniquement les éléments localisables de l'interface utilisateur, tels que les chaînes, les messages d'erreur, les boîtes de dialogue, les menus, les ressources d'objet incorporé, etc., pour la culture neutre.  Le bloc de code contient uniquement le code de l'application à utiliser pour toutes les cultures prises en charge.  Le Common Language Runtime prend en charge un modèle de ressource d'assembly satellite qui sépare le code exécutable d'une application de ses ressources.  Pour plus d'informations sur l'implémentation de ce modèle, consultez [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md).  
  
 Pour chaque version localisée de votre application, ajoutez un nouvel assembly satellite contenant le bloc d'interface utilisateur localisé, traduit dans la langue appropriée pour la culture cible.  Le bloc de code pour toutes les cultures doit rester inchangé.  L'association d'une version localisée du bloc d'interface utilisateur avec le bloc de code produit une version localisée de votre application.  
  
 Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournit le Windows Forms Resource Editor \(Winres.exe\) qui vous permet de localiser rapidement des Windows Forms pour les cultures cibles.  Pour plus d'informations sur l'utilisation de cet outil, consultez [Winres.exe \(Windows Forms Resource Editor\)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## Voir aussi  
 [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)   
 [Révision de l'adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md)   
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)   
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)
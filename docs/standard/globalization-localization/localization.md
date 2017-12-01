---
title: Localisation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture, localization
- application development [.NET Framework], localization
- globalization [.NET Framework], localization
- code blocks
- international applications [.NET Framework], localization
- global applications, localization
- world-ready applications, localization
- user interface blocks
- localization [.NET Framework], about localization
- localizing resources
ms.assetid: 49d520d7-92d7-44ee-bb24-8b615db1d41b
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4aaf2da77a1fab55cbebd6bfa05a2b1c74e5cbbd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="localization"></a>Localisation
La localisation consiste à traduire des ressources d’une application dans les versions localisées pour chaque culture que l’application prend en charge. Vous devez passer à l’étape de localisation uniquement après avoir effectué la [adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md) étape pour vérifier que l’application globalisée est prête pour la localisation.  
  
 Une application est prête pour la localisation est divisée en deux blocs conceptuels, un bloc qui contient tous les éléments d’interface utilisateur et un bloc qui contienne du code exécutable. Le bloc d’interface utilisateur contienne uniquement les éléments d’interface utilisateur localisables telles que les chaînes, les messages d’erreur, boîtes de dialogue, les menus, les ressources d’objet incorporé, et ainsi de suite de la culture neutre. Le bloc de code contient uniquement le code d’application à utiliser par toutes les cultures prises en charge. Le common language runtime prend en charge un modèle de ressource d’assembly satellite qui sépare le code exécutable d’une application à partir de ses ressources. Pour plus d’informations sur l’implémentation de ce modèle, consultez [ressources dans les applications de bureau](../../../docs/framework/resources/index.md).  
  
 Pour chaque version localisée de votre application, ajoutez un nouvel assembly satellite contenant le bloc d’interface utilisateur localisée traduit dans la langue appropriée pour la culture cible. Le bloc de code pour toutes les cultures doit rester le même. La combinaison d’une version localisée du bloc d’interface utilisateur avec le bloc de code produit une version localisée de votre application.  
  
 Le [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)] fournit le Windows Forms Resource Editor (Winres.exe) qui vous permet de localiser rapidement des Windows Forms pour les cultures cibles. Pour plus d’informations sur l’utilisation de cet outil, consultez [Winres.exe (Windows Forms Resource Editor)](../../../docs/framework/tools/winres-exe-windows-forms-resource-editor.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Globalisation et localisation](../../../docs/standard/globalization-localization/index.md)  
 [Révision de l'adaptabilité](../../../docs/standard/globalization-localization/localizability-review.md)  
 [Globalisation](../../../docs/standard/globalization-localization/globalization.md)  
 [Ressources dans des applications de bureau](../../../docs/framework/resources/index.md)

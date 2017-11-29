---
title: Format de Presse-papiers non valide
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vbrID460
ms.assetid: 71a4a045-65bb-417d-b3bd-99a9fa3c53f6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e7adc417d962de35272319d7dc976b237c7e2b6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="clipboard-format-is-not-valid"></a>Format de Presse-papiers non valide
Le format de Presse-papiers spécifié n’est pas compatible avec la méthode en cours d’exécution. Parmi les causes possibles de cette erreur sont :  
  
-   À l’aide du Presse-papiers `GetText` ou `SetText` méthode avec un format de Presse-papiers autre que `vbCFText` ou `vbCFLink`.  
  
-   À l’aide du Presse-papiers `GetData` ou `SetData` méthode avec un format de Presse-papiers autre que `vbCFBitmap`, `vbCFDIB`, ou `vbCFMetafile`.  
  
-   À l’aide de la `DataObject``GetData` méthode ou `SetData` méthode avec un format de Presse-papiers dans la plage réservée par Microsoft Windows pour des formats (& HC000 - & HFFFF), lorsque ce format de Presse-papiers n’a pas été inscrit auprès de Microsoft Windows.  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Supprimez le format incorrect et spécifier une valide.  
  
## <a name="see-also"></a>Voir aussi  
 [Presse-papiers : ajout d’autres formats](/cpp/mfc/clipboard-adding-other-formats)

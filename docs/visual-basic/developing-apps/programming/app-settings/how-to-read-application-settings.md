---
title: "Guide pratique pour lire des paramètres d&quot;application en Visual Basic | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- reading application settings
- My.Settings object, reading application settings
- application settings, reading
ms.assetid: eb3428ef-115e-49a8-a878-e0613183fee0
caps.latest.revision: 12
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e5ad120e52896476447d892438ed9a5d2979da8c
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-read-application-settings-in-visual-basic"></a>Guide pratique pour lire des paramètres d'application en Visual Basic
Vous pouvez lire un paramètre utilisateur en accédant à la propriété du paramètre dans l’objet `My.Settings`.  
  
 L’objet `My.Settings` expose chaque paramètre en tant que propriété. Le nom de la propriété est le même que le nom du paramètre et le type de la propriété est le même que le type du paramètre. La **portée** du paramètre indique si la propriété est en lecture seule. La propriété d’un paramètre de portée **Application** est en lecture seule, tandis que la propriété d’un paramètre de portée **Utilisateur** est en lecture/écriture. Pour plus d’informations, consultez [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md).  
  
## <a name="example"></a>Exemple  
 Cet exemple affiche la valeur du paramètre `Nickname`.  
  
 [!code-vb[VbVbalrMyResources#14](../../../../visual-basic/developing-apps/programming/app-settings/codesnippet/VisualBasic/how-to-read-application-settings_1.vb)]  
  
 Pour que cet exemple fonctionne, votre application doit avoir un paramètre `Nickname` de type `String`. Pour plus d'informations, consultez [Gestion des paramètres d’une application (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet).  
  
## <a name="see-also"></a>Voir aussi  
 [My.Settings, objet](../../../../visual-basic/language-reference/objects/my-settings-object.md)   
 [Guide pratique pour modifier les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-change-user-settings.md)   
 [Guide pratique pour rendre persistants les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-persist-user-settings.md)   
 [Guide pratique pour créer des grilles de propriétés pour les paramètres utilisateur en Visual Basic](../../../../visual-basic/developing-apps/programming/app-settings/how-to-create-property-grids-for-user-settings.md)   
 [Gestion des paramètres d’une application (.NET)](https://docs.microsoft.com/visualstudio/ide/managing-application-settings-dotnet)

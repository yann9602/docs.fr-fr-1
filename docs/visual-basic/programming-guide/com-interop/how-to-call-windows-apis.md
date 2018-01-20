---
title: "Comment : appeler des API Windows (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- API calls [Visual Basic]
- Windows API, calling
- API calls [Visual Basic], platform invoke
- calls [Visual Basic], stored procedures
ms.assetid: 27d75f0a-54ab-4ee1-b91d-43513a19b12d
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 772db789fba4552a4645d2c6a242ba01944652ee
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-call-windows-apis-visual-basic"></a>Comment : appeler des API Windows (Visual Basic)
Cet exemple définit et appelle la `MessageBox` fonction dans user32.dll et lui passe une chaîne.  
  
## <a name="example"></a>Exemple  
 [!code-vb[VbVbalrInterop#1](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/how-to-call-windows-apis_1.vb)]  
  
## <a name="compiling-the-code"></a>Compilation du code  
 Cet exemple nécessite :  
  
-   une référence à l'espace de noms <xref:System>.  
  
## <a name="robust-programming"></a>Programmation fiable  
 Les conditions ci-dessous peuvent générer une exception.  
  
-   La méthode n’est pas statique, est abstraite ou a été définie précédemment. Le type parent est une interface, ou la longueur de *nom* ou *dllName* est égal à zéro. (<xref:System.ArgumentException>)  
  
-   Le *nom* ou *dllName* est `Nothing`. (<xref:System.ArgumentNullException>)  
  
-   Le type conteneur a déjà été créé à l’aide de `CreateType`. (<xref:System.InvalidOperationException>)  
  
## <a name="see-also"></a>Voir aussi  
 [L’appel de plateforme plus approfondie](http://msdn.microsoft.com/library/ba9dd55b-2eaa-45cd-8afd-75cb8d64d243)  
 [Exemples d'appel de code non managé](../../../framework/interop/platform-invoke-examples.md)  
 [Consommation de fonctions DLL non managées](../../../framework/interop/consuming-unmanaged-dll-functions.md)  
 [Émission de la définition d’une méthode avec la réflexion](http://msdn.microsoft.com/library/84fd3bf6-628f-41aa-83d9-b990cf926e81)  
 [Procédure pas à pas : appel des API Windows](../../../visual-basic/programming-guide/com-interop/walkthrough-calling-windows-apis.md)  
 [COM Interop](../../../visual-basic/programming-guide/com-interop/index.md)

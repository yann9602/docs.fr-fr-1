---
title: "Non accessible &#39; Principaux &#39; méthode avec une signature appropriée a été trouvé dans &#39; &lt;nom&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30737
- vbc30737
helpviewer_keywords: BC30737
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e6a2d66c860b72bd3ef59c02f548ac563fab6b8c
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="no-accessible-39main39-method-with-an-appropriate-signature-was-found-in-39ltnamegt39"></a>Non accessible &#39; Principaux &#39; méthode avec une signature appropriée a été trouvé dans &#39; &lt;nom&gt;&#39;
Les applications de ligne de commande doivent avoir un `Sub Main` défini. `Main`doit être déclarée comme `Public Shared` si elle est définie dans une classe, ou en tant que `Public` s’il est défini dans un module.  
  
 **ID d’erreur :** BC30737  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Définir un `Public Sub Main` procédure pour votre projet. Déclarez-le en tant que `Shared` si et seulement si vous la définissez au sein d’une classe.  
  
## <a name="see-also"></a>Voir aussi  
 [Structure d’un programme Visual Basic](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)  
 [Procédures](../../../visual-basic/programming-guide/language-features/procedures/index.md)

---
title: "Type de &#39; &lt;typename&gt;&#39; n’est pas défini"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
helpviewer_keywords: BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 68eb37f43600c51dc9117c3785a12e3c8ede1965
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Type de &#39; &lt;typename&gt;&#39; n’est pas défini
L’instruction a fait référence à un type qui n’a pas été défini. Vous pouvez définir un type dans une instruction de déclaration, tel que `Enum`, `Structure`, `Class`, ou `Interface`.  
  
 **ID d’erreur :** BC30002  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Assurez-vous que la définition de type et sa référence utilisent tous deux la même orthographe.  
  
-   Assurez-vous que la définition de type est accessible à la référence. Par exemple, si le type est dans un autre module et a été déclaré `Private`, déplacez la définition de type vers le module de référence ou déclarez-le `Public`.  
  
-   Assurez-vous que l’espace de noms du type n’est pas redéfinie dans votre projet. Si tel est le cas, utilisez le `Global` (mot clé) pour qualifier complètement le nom de type. Par exemple, si un projet définit un espace de noms `System`, le <xref:System.Object?displayProperty=nameWithType> type ne sont pas accessibles, sauf si elle est qualifié avec le `Global` (mot clé) : `Global.System.Object`.  
  
-   Si le type est défini, mais que la bibliothèque d’objets ou la bibliothèque de types dans laquelle il est défini n’est pas inscrit dans [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], cliquez sur **ajouter une référence** sur la **projet** menu et sélectionnez l’objet approprié bibliothèque ou bibliothèque de types.  
  
-   Assurez-vous que le type est dans un assembly qui fait partie du profil .NET Framework ciblé. Pour plus d’informations, consultez [Dépannage des erreurs de ciblage du .NET Framework](/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Voir aussi  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)  
 [Enum (instruction)](../../../visual-basic/language-reference/statements/enum-statement.md)  
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Class (instruction)](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Interface (instruction)](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)

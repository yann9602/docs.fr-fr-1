---
title: "Type &quot;&lt;typename&gt;&quot; n’est pas défini | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30002
- bc30002
dev_langs:
- VB
helpviewer_keywords:
- BC30002
ms.assetid: b0faf204-57fd-44de-8c05-9db027eea663
caps.latest.revision: 18
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 09aa7c535fd5e17ddcd0e743fb5ec17ebadd4f7d
ms.lasthandoff: 03/13/2017

---
# <a name="type-39lttypenamegt39-is-not-defined"></a>Type '&lt;typename&gt;' n’est pas défini
L’instruction a fait référence à un type qui n’a pas été défini. Vous pouvez définir un type dans une instruction de déclaration, tel que `Enum`, `Structure`, `Class`, ou `Interface`.  
  
 **ID d’erreur :** BC30002  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Vérifiez que la définition de type et sa référence utilisent tous deux la même orthographe.  
  
-   Assurez-vous que la définition de type est accessible à la référence. Par exemple, si le type est dans un autre module et a été déclaré `Private`, déplacez la définition de type vers le module de référence ou déclarez-le `Public`.  
  
-   Assurez-vous que l’espace de noms du type n’est pas redéfinie dans votre projet. Dans le cas, utilisez le `Global` (mot clé) pour qualifier complètement le nom de type. Par exemple, si un projet définit un espace de noms `System`, le <xref:System.Object?displayProperty=fullName>type n’est pas accessible sauf s’il est qualifié avec le `Global` mot clé : `Global.System.Object`.</xref:System.Object?displayProperty=fullName>  
  
-   Si le type est défini, mais la bibliothèque d’objets ou la bibliothèque de type dans lequel il est défini n’est pas enregistré dans [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], cliquez sur **ajouter une référence** sur la **projet** menu, puis sélectionnez la bibliothèque d’objets appropriée ou la bibliothèque de types.  
  
-   Assurez-vous que le type est dans un assembly qui fait partie du profil .NET Framework ciblé. Pour plus d’informations, consultez [erreurs de ciblage de .NET Framework dépannage](https://docs.microsoft.com/visualstudio/msbuild/troubleshooting-dotnet-framework-targeting-errors).  
  
## <a name="see-also"></a>Voir aussi  
 [Espaces de noms dans Visual Basic](../../../visual-basic/programming-guide/program-structure/namespaces.md)   
 [Enum, instruction](../../../visual-basic/language-reference/statements/enum-statement.md)   
 [Structure (instruction)](../../../visual-basic/language-reference/statements/structure-statement.md)   
 [Class, instruction](../../../visual-basic/language-reference/statements/class-statement.md)   
 [Interface, instruction](../../../visual-basic/language-reference/statements/interface-statement.md)   
 [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)

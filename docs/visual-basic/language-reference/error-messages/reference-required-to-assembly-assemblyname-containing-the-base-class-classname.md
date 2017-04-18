---
title: "Référence à l’assembly requise &quot;&lt;assemblyname&gt;&quot;contenant la classe de base&quot;&lt;classname&gt;&quot; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
dev_langs:
- VB
helpviewer_keywords:
- BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 2692478864007c787eb19367109e6ce01882ffb1
ms.lasthandoff: 03/13/2017

---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>Référence à l’assembly requise '&lt;assemblyname&gt;'contenant la classe de base'&lt;classname&gt;»
Référence à l’assembly requise '\<assemblyname >' contenant la classe de base\<classname > ». Ajoutez-en une à votre projet.  
  
 La classe est définie dans une bibliothèque de liens dynamiques (DLL) ou un assembly qui n’est pas directement référencé dans votre projet. Le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] compilateur requiert une référence afin d’éviter toute ambiguïté au cas où la classe est définie dans plusieurs DLL ou assemblys.  
  
 **ID d’erreur :** BC30007  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.  
  
## <a name="see-also"></a>Voir aussi  
 [NIB Guide pratique pour ajouter ou supprimer des références à l’aide de la boîte de dialogue Ajouter une référence](http://msdn.microsoft.com/en-us/3bd75d61-f00c-47c0-86a2-dd1f20e231c9)   
 [Gestion des références dans un projet](https://docs.microsoft.com/visualstudio/ide/managing-references-in-a-project)   
 [Dépannage de références rompues](https://docs.microsoft.com/visualstudio/ide/troubleshooting-broken-references)

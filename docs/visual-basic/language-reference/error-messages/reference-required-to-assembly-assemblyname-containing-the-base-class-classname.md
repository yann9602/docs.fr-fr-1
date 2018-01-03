---
title: "Référence à l’assembly &#39; requise &lt;assemblyname&gt;&#39; contenant la classe de base &#39;&lt; ClassName&gt;&#39;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30007
- vbc30007
helpviewer_keywords: BC30007
ms.assetid: 5f34cf47-6c6e-4954-bd8e-d6b020b75fb7
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 39fa33a655b311ee39466c18cefdb0bf07a92720
ms.sourcegitcommit: 34ec7753acf76f90a0fa845235ef06663dc9e36e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="reference-required-to-assembly-39ltassemblynamegt39-containing-the-base-class-39ltclassnamegt39"></a>Référence à l’assembly &#39; requise &lt;assemblyname&gt;&#39; contenant la classe de base &#39;&lt; ClassName&gt;&#39;
Référence à l’assembly requise '\<nom_assembly >' contenant la classe de base\<nom_classe >'. Ajoutez-en une à votre projet.  
  
 La classe est définie dans une bibliothèque de liens dynamiques (DLL) ou un assembly qui n’est pas directement référencé dans votre projet. Le compilateur [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] nécessite une référence pour éviter toute ambiguïté au cas où la classe serait définie dans plusieurs DLL ou assemblys.  
  
 **ID d’erreur :** BC30007  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Incluez le nom de la DLL ou de l’assembly non référencé dans vos références de projet.  
  
## <a name="see-also"></a>Voir aussi  
   
 [Gestion des références dans un projet](/visualstudio/ide/managing-references-in-a-project)  
 [Dépannage de références rompues](/visualstudio/ide/troubleshooting-broken-references)

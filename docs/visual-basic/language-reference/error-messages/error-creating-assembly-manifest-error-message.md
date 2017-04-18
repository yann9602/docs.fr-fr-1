---
title: "Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt; | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30140
- vbc30140
dev_langs:
- VB
helpviewer_keywords:
- BC30140
ms.assetid: 1beb5aa0-7b79-4c85-946b-5c2d0a41d1d2
caps.latest.revision: 13
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 35a912bbcab78178ce636afa550c244823da512c
ms.lasthandoff: 03/13/2017

---
# <a name="error-creating-assembly-manifest-lterror-messagegt"></a>Erreur de création du manifeste d’assembly : &lt;message d’erreur&gt;
Le compilateur [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] appelle Assembly Linker (Al.exe, également appelé Alink) pour générer un assembly avec un manifeste. L'éditeur de liens a signalé une erreur dans la phase de préémission de création de l'assembly.  
  
 Cela peut être dû à des problèmes avec le fichier de clé ou le conteneur de clé indiqué. Pour signer un assembly, vous devez fournir un fichier de clé valide contenant des informations relatives aux clés publiques et privées. Pour différer la signature d’un assembly, vous devez sélectionner le **temporiser la signature uniquement** et fournir un fichier de clé valid qui contient des informations sur les informations de clé publique. La clé privée n'est pas nécessaire quand la signature d'un assembly est différée. Pour plus d’informations, consultez [Comment : signer un Assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564).  
  
 **ID d’erreur :** BC30140  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
1.  Examinez le message d’erreur cité et consultez la rubrique [Al.exe Tool Errors and Warnings](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) erreur AL1019 davantage d’explications et conseils  
  
2.  Si l'erreur persiste, rassemblez des informations sur ses circonstances et avertissez les services de support technique Microsoft.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide pratique pour signer un assembly (Visual Studio)](http://msdn.microsoft.com/en-us/f468a7d3-234c-4353-924d-8e0ae5896564)   
 [Page Signature, Concepteur de projet](https://docs.microsoft.com/visualstudio/ide/reference/signing-page-project-designer)   
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)   
 [Avertissements et erreurs de l’outil Al.exe](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)   
 [Nous contacter](https://docs.microsoft.com/visualstudio/ide/talk-to-us)

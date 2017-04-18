---
title: "Résolution à liaison tardive ; erreurs d’exécution peuvent se produire | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42017
- BC42017
dev_langs:
- VB
helpviewer_keywords:
- BC42017
ms.assetid: 45f552c8-57c6-44c0-97d3-e510119b257a
caps.latest.revision: 12
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
ms.openlocfilehash: 3ac885b0de2c4f44d4323487fc55cde9b23defa4
ms.lasthandoff: 03/13/2017

---
# <a name="late-bound-resolution-runtime-errors-could-occur"></a>Résolution à liaison tardive ; des erreurs d’exécution peuvent se produire
Un objet est assigné à une variable déclarée comme le [Type de données Object](../../../visual-basic/language-reference/data-types/object-data-type.md).  
  
 Lorsque vous déclarez une variable en tant que `Object`, le compilateur doit exécuter *liaison tardive*, ce qui provoque des opérations supplémentaires au moment de l’exécution. Cela expose également votre application à des erreurs d’exécution potentielles. Par exemple, si vous attribuez un <xref:System.Windows.Forms.Form>à la `Object` variable et réessayez d’accéder à la <xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName>propriété, le runtime lève une <xref:System.MemberAccessException>car le <xref:System.Windows.Forms.Form>n’expose pas de classe une `NameTable` propriété.</xref:System.Windows.Forms.Form> </xref:System.MemberAccessException> </xref:System.Xml.XmlDocument.NameTable%2A?displayProperty=fullName> </xref:System.Windows.Forms.Form>  
  
 Si vous déclarez la variable comme étant d’un type spécifique, le compilateur peut exécuter *liaison anticipée* au moment de la compilation. Cela entraîne des performances améliorées, un accès contrôlé aux membres du type spécifique et une meilleure lisibilité de votre code.  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42017  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si possible, déclarez la variable comme étant d’un type spécifique.  
  
## <a name="see-also"></a>Voir aussi  
 [Liaison anticipée et liaison tardive](../../../visual-basic/programming-guide/language-features/early-late-binding/index.md)   
 [Déclaration des variables objets](../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md)

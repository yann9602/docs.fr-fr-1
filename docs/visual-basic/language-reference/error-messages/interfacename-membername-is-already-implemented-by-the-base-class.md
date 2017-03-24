---
title: "«&lt;interfacename&gt;.&lt; MemberName&gt;&quot;est déjà implémenté par la classe de base&quot;&lt;baseclassname&gt;». Réimplémentation de &lt;type&gt; supposé | Documents Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc42015
- bc42015
dev_langs:
- VB
helpviewer_keywords:
- BC42015
ms.assetid: 658c070a-113e-4bd8-b294-12c243191160
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 5ab2041826f74fdc5aceab7b1ceb26563d9b3f0a
ms.lasthandoff: 03/13/2017

---
# <a name="39ltinterfacenamegtltmembernamegt39-is-already-implemented-by-the-base-class-39ltbaseclassnamegt39-re-implementation-of-lttypegt-assumed"></a>«&lt;interfacename&gt;.&lt; MemberName&gt;'est déjà implémenté par la classe de base'&lt;baseclassname&gt;». Réimplémentation de &lt;type&gt; supposé
Une propriété, une procédure ou un événement dans une classe dérivée utilise un `Implements` clause qui spécifie un membre d’interface qui est déjà implémenté dans la classe de base.  
  
 Une classe dérivée peut réimplémenter un membre d’interface qui est implémenté par sa classe de base. La substitution de l’implémentation de la classe de base est une procédure différente. Pour plus d’informations, consultez [implémente](../../../visual-basic/language-reference/statements/implements-clause.md).  
  
 Par défaut, ce message est un avertissement. Pour plus d’informations sur le masquage des avertissements ou leur traitement en tant qu’erreurs, consultez [Configuring Warnings in Visual Basic](https://docs.microsoft.com/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID d’erreur :** BC42015  
  
## <a name="to-correct-this-error"></a>Pour corriger cette erreur  
  
-   Si vous comptez réimplémenter le membre d’interface, aucune mesure n’est nécessaire. Le code dans votre classe dérivée accède au membre implémenté de nouveau, sauf si vous utilisez la `MyBase` mot clé pour accéder à l’implémentation de classe de base.  
  
-   Si vous ne comptez pas réimplémenter le membre d’interface, supprimez la clause `Implements` de la déclaration de la propriété, de la procédure ou de l’événement.  
  
## <a name="see-also"></a>Voir aussi  
 [Interfaces](../../../visual-basic/programming-guide/language-features/interfaces/index.md)

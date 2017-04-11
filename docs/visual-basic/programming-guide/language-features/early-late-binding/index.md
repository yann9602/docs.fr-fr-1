---
title: "Liaison anticipée et liaison tardive (Visual Basic) | Microsoft Docs"
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
- early binding
- objects [Visual Basic], late-bound
- objects [Visual Basic], early-bound
- objects [Visual Basic], late bound
- early binding, Visual Basic compiler
- binding, late and early
- objects [Visual Basic], early bound
- Visual Basic compiler, early and late binding
- late binding
- late binding, Visual Basic compiler
ms.assetid: d6ff7f1e-b94f-4205-ab8d-5cfa91758724
caps.latest.revision: 10
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
ms.openlocfilehash: 157e1000c30c688ac489d468dcaf9f93b8934002
ms.lasthandoff: 03/13/2017

---
# <a name="early-and-late-binding-visual-basic"></a>Liaison anticipée et liaison tardive (Visual Basic)
Le compilateur [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] exécute un processus appelé `binding` lorsqu’un objet est affecté à une variable objet. Un objet est dit *à liaison anticipée* lorsqu’il est affecté à une variable déclarée comme étant d’un type d’objet spécifique. Les objets à liaison anticipée permettent au compilateur d’allouer de la mémoire et d’effectuer d’autres optimisations avant l’exécution d’une application. Par exemple, le fragment de code suivant déclare une variable de type <xref:System.IO.FileStream> :  
  
 [!code-vb[VbVbalrOOP#90](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_1.vb)]  
  
 Étant donné que <xref:System.IO.FileStream> est un type d’objet spécifique, l’instance affectée à `FS` est à liaison anticipée.  
  
 Par opposition, un objet est dit *à liaison tardive* lorsqu’il est affecté à une variable déclarée comme étant du type `Object`. Les objets de ce type peuvent contenir des références à n’importe quel objet, mais ne présentent pas tous les avantages des objets à liaison anticipée. Par exemple, le fragment de code suivant déclare une variable objet qui contient un objet retourné par la fonction `CreateObject` :  
  
 [!code-vb[VbVbalrOOP#91](../../../../visual-basic/misc/codesnippet/VisualBasic/early-and-late-binding_2.vb)]  
  
## <a name="advantages-of-early-binding"></a>Avantages de la liaison anticipée  
 Utilisez des objets à liaison anticipée chaque fois que c’est possible, car ils permettent au compilateur d’effectuer d’importantes optimisations qui génèrent des applications plus efficaces. Les objets à liaison anticipée sont considérablement plus rapides que les objets à liaison tardive et rendent votre code plus facile à lire et à gérer en indiquant exactement quels types d’objets sont utilisés. La liaison anticipée présente également l’avantage d’offrir des fonctions utiles, comme la saisie semi-automatique de code et l’aide dynamique, car l’environnement de développement intégré (IDE) [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs_md.md)] peut déterminer avec précision le type d’objet utilisé lorsque vous modifiez le code. Elle réduit le nombre et la gravité des erreurs d’exécution, car elle permet au compilateur de signaler des erreurs à la compilation du programme.  
  
> [!NOTE]
>  La liaison tardive ne peut être utilisée que pour accéder aux membres de type déclarés comme `Public`. L’accès aux membres déclarés comme `Friend` ou `Protected Friend` provoque une erreur d’exécution.  
  
## <a name="see-also"></a>Voir aussi  
 <xref:Microsoft.VisualBasic.Interaction.CreateObject%2A>   
 [Durée de vie d’un objet : création et destruction des objets](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)   
 [Object (type de données)](../../../../visual-basic/language-reference/data-types/object-data-type.md)

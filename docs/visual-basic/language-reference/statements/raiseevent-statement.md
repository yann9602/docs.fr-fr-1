---
title: RaiseEvent, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RaiseEventMethod
- vb.RaiseEvent
- RaiseEvent
helpviewer_keywords:
- raising events [Visual Basic], RaiseEvent statement
- RaiseEvent statement [Visual Basic]
- event handlers, connecting events to
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 2575598577820bd7a72fae2d9b8ba52978f5952d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="raiseevent-statement"></a>RaiseEvent, instruction
Déclenche un événement déclaré au niveau du module dans une classe, un formulaire ou un document.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## <a name="parts"></a>Composants  
 `eventname`  
 Obligatoire. Nom de l’événement à déclencher.  
  
 `argumentlist`  
 Facultatif. Liste délimitée par des virgules des variables, des tableaux ou des expressions. Le `argumentlist` argument doit être mis entre parenthèses. S’il n’y a pas d’arguments, les parenthèses doivent être omis.  
  
## <a name="remarks"></a>Remarques  
 Requis `eventname` est le nom d’un événement déclaré dans le module. Il suit les conventions d’affectation des noms variables de Visual Basic.  
  
 Si l’événement n’a pas été déclaré dans le module dans lequel il est déclenché, une erreur se produit. Le fragment de code suivant illustre une déclaration d’événement et d’une procédure dans laquelle l’événement est déclenché.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_1.vb)]  
  
 Vous ne pouvez pas utiliser `RaiseEvent` pour déclencher des événements qui ne sont pas explicitement déclarés dans le module. Par exemple, tous les formulaires héritent un <xref:System.Windows.Forms.Control.Click> événement à partir de <xref:System.Windows.Forms.Form?displayProperty=nameWithType>, il ne peut pas être déclenché à l’aide de `RaiseEvent` dans un formulaire dérivé. Si vous déclarez un `Click` événement dans le module du formulaire, elle occulte du formulaire propre <xref:System.Windows.Forms.Control.Click> événement. Vous pouvez toujours appeler du formulaire <xref:System.Windows.Forms.Control.Click> événement en appelant le <xref:System.Windows.Forms.Control.OnClick%2A> (méthode).  
  
 Par défaut, un événement défini en Visual Basic déclenche ses gestionnaires d’événements dans l’ordre que les connexions sont établies. Étant donné que les événements peuvent disposer de `ByRef` paramètres, un processus qui se connecte ultérieurement peut recevoir des paramètres qui ont été modifiés par un gestionnaire d’événements précédent. Une fois que les gestionnaires d’événements est exécuté, le contrôle est retourné à la sous-routine qui a déclenché l’événement.  
  
> [!NOTE]
>  Les événements non partagés ne doivent pas être déclenchés dans le constructeur de la classe dans laquelle elles sont déclarées. Bien que ces événements ne provoquent pas d’erreurs d’exécution, ils peuvent ne pas être interceptée par les gestionnaires d’événements associés. Utilisez le `Shared` modificateur pour créer un événement partagé Si vous avez besoin déclencher un événement à partir d’un constructeur.  
  
> [!NOTE]
>  Vous pouvez modifier le comportement par défaut des événements en définissant un événement personnalisé. Pour les événements personnalisés, les `RaiseEvent` instruction appelle l’événement `RaiseEvent` accesseur. Pour plus d’informations sur les événements personnalisés, consultez [Event, instruction](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## <a name="example"></a>Exemple  
 L'exemple suivant utilise des événements pour décompter les secondes de 10 à 0. Le code illustre plusieurs méthodes relatives aux événements, des propriétés et des instructions, y compris la `RaiseEvent` instruction.  
  
 La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements. Une source d'événement peut avoir plusieurs gestionnaires pour les événements qu'elle génère. Quand la classe déclenche l'événement, celui-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.  
  
 L'exemple utilise également un formulaire (`Form1`) avec un bouton (`Button1`) et une zone de texte (`TextBox1`). Quand vous cliquez sur le bouton, la première zone de texte affiche un compte à rebours de 10 à 0 secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
 Le code correspondant à `Form1` indique les états de début et de fin du formulaire. Il contient également le code exécuté lors du déclenchement des événements.  
  
 Pour utiliser cet exemple, ouvrez un nouveau projet d’Application Windows, ajoutez un bouton nommé `Button1` et une zone de texte nommée `TextBox1` au formulaire principal, nommé `Form1`. Cliquez sur le formulaire, puis cliquez sur **afficher le Code** pour ouvrir l’éditeur de Code.  
  
 Ajouter un `WithEvents` à la section des déclarations de variable la `Form1` classe.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_2.vb)]  
  
## <a name="example"></a>Exemple  
 Ajoutez le code suivant au code pour `Form1`. Remplacez toute procédure en double peut-être exister, tel que `Form_Load`, ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/raiseevent-statement_3.vb)]  
  
 Appuyez sur F5 pour exécuter l’exemple précédent, puis cliquez sur le bouton intitulé **Démarrer**. La première zone de texte commence à décompter les secondes. Quand la durée totale (10 secondes) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
> [!NOTE]
>  Le `My.Application.DoEvents` méthode ne traite pas les événements dans la même façon que le formulaire. Pour permettre au formulaire gérer les événements directement, vous pouvez utiliser le multithreading. Pour plus d’informations, consultez [Threading](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c).  
  
## <a name="see-also"></a>Voir aussi  
 [Événements](../../../visual-basic/programming-guide/language-features/events/index.md)  
 [Event (instruction)](../../../visual-basic/language-reference/statements/event-statement.md)  
 [AddHandler (instruction)](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [RemoveHandler (instruction)](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)

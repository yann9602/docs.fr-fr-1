---
title: "RaiseEvent Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.RaiseEventMethod"
  - "vb.RaiseEvent"
  - "RaiseEvent"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "raising events, RaiseEvent statement"
  - "RaiseEvent statement"
  - "event handlers, connecting events to"
ms.assetid: f82e380a-1e6b-4047-bea8-c853f4d2c742
caps.latest.revision: 19
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 19
---
# RaiseEvent Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Déclenche un événement déclaré au niveau module dans une classe, un formulaire ou un document.  
  
## Syntaxe  
  
```  
RaiseEvent eventname[( argumentlist )]  
```  
  
## Composants  
 `eventname`  
 Obligatoire.  Nom de l'événement à déclencher.  
  
 `argumentlist`  
 Facultatif.  Liste délimitée par des virgules énumérant des variables, des tableaux ou des expressions.  L'argument `argumentlist` doit être mis entre parenthèses.  En cas d'absence d'argument, les parenthèses doivent être supprimées.  
  
## Notes  
 Le paramètre `eventname` requis correspond au nom d'un événement déclaré dans le module.  Il suit les conventions d'affectation de nom de variables Visual Basic.  
  
 Si l'événement n'a pas été déclaré dans le module dans lequel il est déclenché, une erreur se produit.  Le fragment de code suivant illustre une déclaration de l'événement et une procédure dans laquelle l'événement est déclenché.  
  
 [!code-vb[VbVbalrEvents#37](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#37)]  
  
 Vous ne pouvez pas utiliser `RaiseEvent` pour générer des événements qui ne sont pas déclarés de façon explicite dans le module.  Par exemple, tous les formulaires héritent d'un événement <xref:System.Windows.Forms.Control.Click> de <xref:System.Windows.Forms.Form?displayProperty=fullName> ; il ne peut pas être déclenché à l'aide de `RaiseEvent` dans un formulaire dérivé.  Si vous déclarez un événement `Click` dans le module formulaire, celui\-ci occulte l'événement <xref:System.Windows.Forms.Control.Click> appartenant au formulaire.  Vous pouvez toujours appeler l'événement <xref:System.Windows.Forms.Control.Click> du formulaire en appelant la méthode <xref:System.Windows.Forms.Control.OnClick%2A>.  
  
 Par défaut, un événement défini en Visual Basic déclenche ses gestionnaires d'événements suivant l'ordre dans lequel les connexions sont établies.  Dans la mesure où les événements peuvent comporter des paramètres `ByRef`, un processus qui se connecte ultérieurement peut recevoir des paramètres ayant été modifiés par un gestionnaire d'événements précédent.  Une fois que les gestionnaires d'événements s'exécutent, le contrôle est retourné à la sous\-routine qui a déclenché l'événement.  
  
> [!NOTE]
>  Les événements non partagés ne doivent pas être déclenchés dans le constructeur de la classe dans laquelle ils sont déclarés.  Bien que de tels événements ne causent pas d'erreurs à l'exécution, ils peuvent ne pas être détectés par des gestionnaires d'événements associés.  Utilisez le modificateur `Shared` pour créer un événement partagé si vous avez besoin de déclencher un événement à partir d'un constructeur.  
  
> [!NOTE]
>  Vous pouvez modifier le comportement par défaut des événements en définissant un événement personnalisé.  Pour les événements personnalisés, l'instruction `RaiseEvent` appelle l'accesseur `RaiseEvent` de l'événement.  Pour plus d'informations sur les événements personnalisés, consultez [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).  
  
## Exemple  
 L'exemple suivant utilise des événements pour compter les secondes de 10 à 0.  Le code illustre plusieurs méthodes, propriétés et instructions liées à des événements, y compris l'instruction `RaiseEvent`.  
  
 La classe qui déclenche un événement est la source de l'événement, et les méthodes qui traitent l'événement sont les gestionnaires d'événements.  Une source d'événement peut avoir des gestionnaires multiples pour les événements qu'elle génère.  Lorsque la classe génère l'événement, celui\-ci se produit pour chaque classe ayant choisi de gérer les événements pour cette instance de l'objet.  
  
 Cet exemple utilise aussi un formulaire \(`Form1`\) comportant un bouton \(`Button1`\) et une zone de texte \(`TextBox1`\).  Lorsque vous cliquez sur le bouton, la première zone affiche un compte à rebours de 10 à 0 secondes.  Lorsque la durée totale \(10 secondes\) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
 Le code correspondant à `Form1` indique les états de début et de fin du formulaire.  Il contient également le code exécuté lors du déclenchement des événements.  
  
 Pour utiliser cet exemple, ouvrez un nouveau projet d'application Windows, ajoutez un bouton appelé `Button1` et une zone de texte appelée `TextBox1` au formulaire principal appelé `Form1`.  Cliquez ensuite avec le bouton droit sur le formulaire, puis cliquez sur **Afficher le code** pour ouvrir l'éditeur de code.  
  
 Ajoutez une variable `WithEvents` à la section des déclarations de la classe `Form1`.  
  
 [!code-vb[VbVbalrEvents#14](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#14)]  
  
## Exemple  
 Ajoutez le code suivant au code pour `Form1`.  Remplacez toute procédure en double éventuelle, telle que `Form_Load` ou `Button_Click`.  
  
 [!code-vb[VbVbalrEvents#15](../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#15)]  
  
 Appuyez sur F5 pour exécuter l'exemple précédent, puis cliquez sur le bouton **Démarrer**.  La première zone de texte commence le compte à rebours des secondes.  Lorsque la durée totale \(10 secondes\) s'est écoulée, la première zone de texte affiche « Terminé ».  
  
> [!NOTE]
>  La méthode `My.Application.DoEvents` ne traite pas les événements exactement de la même manière que le formulaire.  Pour permettre au formulaire de gérer les événements directement, vous pouvez utiliser le multithreading.  Pour plus d'informations, consultez [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md).  
  
## Voir aussi  
 [Events](../../../visual-basic/programming-guide/language-features/events/events.md)   
 [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md)   
 [AddHandler Statement](../../../visual-basic/language-reference/statements/addhandler-statement.md)   
 [RemoveHandler Statement](../../../visual-basic/language-reference/statements/removehandler-statement.md)   
 [Handles](../../../visual-basic/language-reference/statements/handles-clause.md)
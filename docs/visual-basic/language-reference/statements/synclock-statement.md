---
title: "SyncLock Statement | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.SyncLock"
  - "SyncLock"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "threading [Visual Basic], locks"
  - "SyncLock statement"
  - "locks, threads"
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: 17
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 17
---
# SyncLock Statement
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Acquiert un verrou exclusif pour un bloc d'instruction avant d'exécuter le bloc.  
  
## Syntaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## Composants  
 `lockobject`  
 Requis.  Expression qui prend la valeur d'une référence d'objet.  
  
 `block`  
 Optionnel.  Bloc d'instructions qui doivent être exécutées lorsque le verrou est acquis.  
  
 `End SyncLock`  
 Met fin à un bloc `SyncLock`.  
  
## Notes  
 L'instruction `SyncLock` garantit que plusieurs threads n'exécutent pas le bloc d'instructions en même temps.  `SyncLock` empêche chaque thread d'entrer dans le bloc jusqu'à ce qu'aucun autre thread ne l'exécute.  
  
 L'utilisation la plus courante de `SyncLock` est d'empêcher la mise à jour des données par plusieurs threads simultanément.  Si les instructions qui manipulent les données doivent être exécutées sans interruption, mettez\-les dans un bloc `SyncLock`.  
  
 Un bloc d'instruction protégé par un verrou exclusif est parfois appelé une *section critique*.  
  
## Règles  
  
-   Branchement.  Vous ne pouvez pas vous brancher dans un bloc `SyncLock` de l'extérieur du bloc.  
  
-   Valeur de l'objet lock.  La valeur de `lockobject` ne peut pas être `Nothing`.  Vous devez créer l'objet lock avant de l'utiliser dans une instruction `SyncLock`.  
  
     Vous ne pouvez pas modifier la valeur de `lockobject` en exécutant un bloc `SyncLock`.  Le mécanisme exige que l'objet lock reste inchangé.  
  
-   Vous ne pouvez pas utiliser l'opérateur d' [attendez](../../../visual-basic/language-reference/operators/await-operator.md) dans un bloc d' `SyncLock` .  
  
## Comportement  
  
-   Mécanisme.  Lorsqu'un thread atteint l'instruction `SyncLock`, il évalue l'expression `lockobject` et interrompt l'exécution jusqu'à ce qu'il acquière un verrou exclusif sur l'objet retourné par l'expression.  Lorsqu'un autre thread atteint l'instruction `SyncLock`, il n'acquiert pas de verrou jusqu'à ce que le premier thread exécute l'instruction `End SyncLock`.  
  
-   Données protégées.  Si `lockobject` est une variable `Shared`, le verrou exclusif empêche un tread d'exécuter le bloc `SyncLock` dans toute instance de la classe pendant qu'un autre l'exécute.  Cela protège des données qui sont partagées par toutes les instances.  
  
     Si `lockobject` est une variable d'instance \(non `Shared`\), le verrou empêche un thread qui s'exécute dans l'instance en cours d'exécuter le bloc `SyncLock` en même temps qu'un autre thread dans la même instance.  Cela protège des données gérées par l'instance.  
  
-   Acquisition et libération.  Un bloc `SyncLock` se comporte comme une construction `Try...Finally` dans laquelle le bloc `Try` acquiert un verrou exclusif sur `lockobject` et le bloc `Finally` le libère.  C'est pourquoi le bloc `SyncLock` garantit la libération du verrou, peu importe comment vous quittez le bloc.  Cela est vrai même dans le cas d'une exception non gérée.  
  
-   Appels du Framework.  Le bloc `SyncLock` acquiert et libère le verrou exclusif en appelant les méthodes `Enter` et `Exit` de la classe `Monitor` dans l'espace de noms <xref:System.Threading>.  
  
## Méthodes de programmation  
 L'expression `lockobject` doit toujours prendre la valeur d'un objet qui appartient exclusivement à votre classe.  Vous devez déclarer une variable objet `Private` pour protéger des données qui appartiennent à l'instance en cours ou une variable objet `Private Shared` pour protéger des données communes à toutes les instances.  
  
 Vous ne devez pas utiliser le mot clé `Me` pour fournir un objet lock aux données de l'instance.  Si un code externe à votre classe comporte une référence à une instance de votre classe, il pourrait utiliser cette référence comme un objet lock pour un bloc `SyncLock` complètement différent du vôtre, protégeant des données différentes.  De cette manière, votre classe et l'autre classe pourraient s'empêcher l'une l'autre d'exécuter leurs blocs `SyncLock` non liés.  Un verrouillage de ce type sur une chaîne peut poser problème puisque tout autre code du processus utilisant la même chaîne partagera le même verrouillage.  
  
 De même, vous ne devez pas utiliser la méthode `Me.GetType` pour fournir un objet lock aux données partagées.  Cela est dû au fait que `GetType` retourne toujours le même objet `Type` pour un nom de classe donné.  Le code externe pourrait appeler `GetType` de votre classe et obtenir le même objet lock que vous utilisez.  Les deux classes s'empêcheraient l'une l'autre d'exécuter à leurs blocs `SyncLock`.  
  
## Exemples  
  
### Description  
 L'exemple suivant affiche une classe qui gère une liste ordinaire de messages.  Il stocke les messages dans un tableau et le dernier élément utilisé de ce tableau dans une variable.  La procédure `addAnotherMessage` incrémente le dernier élément et stocke le nouveau message.  Ces deux opérations sont protégées par les instructions `SyncLock` et `End SyncLock`, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que tout autre thread puisse incrémenter encore le dernier élément.  
  
 Si la classe `simpleMessageList` partage une liste de messages entre toutes ses instances, les variables `messagesList` et `messagesLast` sont déclarées comme `Shared`.  Dans ce cas, les `messagesLock` de variables doivent être également `Shared`, afin qu'il y ait un objet lock seul utilisé par chaque instance.  
  
### Code  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### Description  
 L'exemple suivant utilise des threads et `SyncLock` :  Tant que l'instruction `SyncLock` est présente, le bloc d'instructions est une section critique et `balance` ne devient jamais un nombre négatif.  Vous pouvez commenter les instructions `SyncLock` et `End SyncLock` pour observer l'effet de la mise à l'écart du mot clé `SyncLock`.  
  
### Code  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### Commentaires  
  
## Voir aussi  
 <xref:System.Threading>   
 <xref:System.Threading.Monitor>   
 [Synchronisation des threads](../Topic/Thread%20Synchronization%20\(C%23%20and%20Visual%20Basic\).md)   
 [Thread](../Topic/Threading%20\(C%23%20and%20Visual%20Basic\).md)
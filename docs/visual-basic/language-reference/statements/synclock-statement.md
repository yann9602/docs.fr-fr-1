---
title: SyncLock, instruction
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.SyncLock
- SyncLock
helpviewer_keywords:
- threading [Visual Basic], locks
- SyncLock statement [Visual Basic]
- locks, threads
ms.assetid: 14501703-298f-4d43-b139-c4b6366af176
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: c0c826e1ba592dfc4f2899a26102466d2e7df54f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="synclock-statement"></a>SyncLock, instruction
Acquiert un verrou exclusif pour un bloc d’instructions avant d’exécuter le bloc.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
SyncLock lockobject  
    [ block ]  
End SyncLock  
```  
  
## <a name="parts"></a>Composants  
 `lockobject`  
 Obligatoire. Expression qui correspond à une référence d’objet.  
  
 `block`  
 Facultatif. Bloc d’instructions à exécuter lorsque le verrou est acquis.  
  
 `End SyncLock`  
 Met fin à une `SyncLock` bloc.  
  
## <a name="remarks"></a>Remarques  
 La `SyncLock` instruction permet de s’assurer que plusieurs threads n’exécutent pas le bloc d’instructions en même temps. `SyncLock`empêche chaque thread d’entrer dans le bloc jusqu'à ce qu’aucun autre thread ne l’exécute.  
  
 L’utilisation la plus courante de `SyncLock` consiste à protéger les données à partir de la mise à jour par plusieurs threads simultanément. Si les instructions qui manipulent les données doivent être exécutées sans interruption, placez-les à l’intérieur d’un `SyncLock` bloc.  
  
 Un bloc d’instruction protégé par un verrou exclusif est parfois appelé un *section critique*.  
  
## <a name="rules"></a>Règles  
  
-   Création de branche. Vous ne pouvez pas créer de branche dans un `SyncLock` blocage à partir de l’extérieur du bloc.  
  
-   Valeur de l’objet verrou. La valeur de `lockobject` ne peut pas être `Nothing`. Vous devez créer l’objet lock avant de l’utiliser dans un `SyncLock` instruction.  
  
     Vous ne pouvez pas modifier la valeur de `lockobject` lors de l’exécution une `SyncLock` bloc. Le mécanisme exige que l’objet verrou reste inchangée.  
  
-   Vous ne pouvez pas utiliser le [Await](../../../visual-basic/language-reference/operators/await-operator.md) opérateur dans un `SyncLock` bloc.  
  
## <a name="behavior"></a>Comportement  
  
-   Mécanisme. Lorsqu’un thread atteint le `SyncLock` instruction, il évalue les `lockobject` expression et suspend l’exécution jusqu'à ce qu’il acquiert un verrou exclusif sur l’objet retourné par l’expression. Lorsqu’un autre thread atteint le `SyncLock` instruction, il n’acquiert pas de verrou jusqu'à ce que le premier thread exécute la `End SyncLock` instruction.  
  
-   Les données protégées. Si `lockobject` est un `Shared` variable, le verrou exclusif empêche un thread dans n’importe quelle instance de la classe à partir de l’exécution de la `SyncLock` bloquer un autre thread est exécutée. Cela protège les données qui sont partagées entre toutes les instances.  
  
     Si `lockobject` est une variable d’instance (non `Shared`), le verrou empêche un thread en cours d’exécution dans l’instance actuelle à partir de l’exécution de la `SyncLock` bloc en même temps qu’un autre thread dans la même instance. Cela protège les données gérées par l’instance.  
  
-   Acquisition et la mise en production. A `SyncLock` bloc se comporte comme un `Try...Finally` dans laquelle le `Try` bloc acquiert un verrou exclusif sur `lockobject` et `Finally` bloc le libère. Pour cette raison, le `SyncLock` bloc garantit la libération du verrou, quel que soit la manière dont vous quittez le bloc. Cela est vrai même en cas d’une exception non gérée.  
  
-   Appels du Framework. Le `SyncLock` bloc acquiert et libère le verrou exclusif en appelant le `Enter` et `Exit` méthodes de la `Monitor` classe dans le <xref:System.Threading> espace de noms.  
  
## <a name="programming-practices"></a>Méthodes de programmation  
 Le `lockobject` expression doit toujours correspondre à un objet qui appartienne exclusivement à votre classe. Vous devez déclarer un `Private` variable objet pour protéger les données appartenant à l’instance actuelle, ou un `Private Shared` variable objet pour protéger les données communes à toutes les instances.  
  
 Vous ne devez pas utiliser le `Me` données mot clé pour fournir un verrou d’objet pour l’instance. Si le code externe à votre classe possède une référence à une instance de votre classe, il peut utiliser cette référence comme un objet lock pour un `SyncLock` bloc complètement différent du vôtre, protégeant des données différentes. De cette façon, votre classe et l’autre classe peuvent bloquer mutuellement à partir de l’exécution de leur relation `SyncLock` blocs. Le verrouillage de la même façon sur une chaîne peut être problématique, car tout autre code dans le processus à l’aide de la même chaîne partagera le même verrou.  
  
 Vous devez également utiliser pas le `Me.GetType` méthode pour fournir un objet de verrouillage pour les données partagées. C’est parce que `GetType` retourne toujours le même `Type` objet pour un nom de classe donné. Le code externe peut appeler `GetType` sur votre classe et obtenir le même objet lock que vous utilisez. Cela entraînerait le blocage de l’autre de deux classes leurs `SyncLock` blocs.  
  
## <a name="examples"></a>Exemples  
  
### <a name="description"></a>Description  
 L’exemple suivant montre une classe qui gère une liste simple de messages. Il stocke les messages dans un tableau et le dernier élément utilisé de ce tableau dans une variable. Le `addAnotherMessage` procédure incrémente le dernier élément et stocke le nouveau message. Ces deux opérations sont protégées par le `SyncLock` et `End SyncLock` instructions, car une fois que le dernier élément a été incrémenté, le nouveau message doit être stocké avant que n’importe quel autre thread puisse incrémenter le dernier élément à nouveau.  
  
 Si le `simpleMessageList` classe partagée d’une liste de messages entre toutes ses instances, les variables `messagesList` et `messagesLast` sont déclarées comme `Shared`. Dans ce cas, la variable `messagesLock` doit également être `Shared`, afin qu’il y ait un objet lock seul utilisé par chaque instance.  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#1](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_1.vb)]  
  
### <a name="description"></a>Description  
 L’exemple suivant utilise des threads et `SyncLock`. Tant que le `SyncLock` instruction est présente, le bloc d’instructions est une section critique et `balance` ne devient jamais un nombre négatif. Vous pouvez placer en commentaire la `SyncLock` et `End SyncLock` instructions pour voir l’effet de la mise la `SyncLock` (mot clé).  
  
### <a name="code"></a>Code  
 [!code-vb[VbVbalrThreading#21](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/synclock-statement_2.vb)]  
  
### <a name="comments"></a>Commentaires  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading>  
 <xref:System.Threading.Monitor>  
 [Synchronisation des threads](http://msdn.microsoft.com/library/413e1f28-a2c5-4eec-8338-aa43e7982ff4)  
 [Thread](http://msdn.microsoft.com/library/552f6c68-dbdb-4327-ae36-32cf9063d88c)

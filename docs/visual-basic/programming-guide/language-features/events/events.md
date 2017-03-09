---
title: "Events (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "02/25/2017"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "events [Visual Basic], about events"
  - "events [Visual Basic]"
ms.assetid: 8fb0353a-e41b-4e23-b78f-da65db832f70
caps.latest.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Events (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez comparer un projet [!INCLUDE[vsprvs](../../../../csharp/includes/vsprvs-md.md)] à une série de procédures qui s'exécutent dans une séquence, mais en réalité, la plupart des programmes sont pilotés par des événements, c'est\-à\-dire que le déroulement de l'exécution dépend d'occurrences externes appelées *événements*.  
  
 Un événement est un signal qui informe l'application que quelque chose d'important s'est produit.  Par exemple, lorsqu'un utilisateur clique sur un contrôle d'un formulaire, le formulaire peut déclencher un événement `Click` et appeler une procédure qui gère l'événement.  Les événements séparent également les tâches pour communiquer.  Supposons, par exemple, que votre application exécute une tâche de tri séparément de l'application principale.  Si un utilisateur annule le tri, votre application peut envoyer un événement d'annulation demandant au processus de tri de s'interrompre.  
  
## Termes et concepts relatifs aux événements  
 Cette section décrit les termes et concepts utilisés avec les événements en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
### Déclaration d'événements  
 Vous déclarez des événements dans le cadre de classes, structures, modules et interfaces à l'aide du mot clé `Event`, comme dans l'exemple suivant :  
  
 [!code-vb[VbVbalrEvents#24](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#24)]  
  
### Déclenchement d'événements  
 Un événement est comparable à un message annonçant que quelque chose d'important s'est produit.  L'acte de diffusion du message est appelé *déclenchement* de l'événement.  En [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)], vous déclenchez des événements à l'aide de l'instruction `RaiseEvent`, comme dans l'exemple suivant :  
  
 [!code-vb[VbVbalrEvents#25](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#25)]  
  
 Les événements doivent être déclenchés dans la portée de la classe, du module ou de la structure où ils sont déclarés.  Par exemple, une classe dérivée ne peut pas déclencher d'événements hérités à partir d'une classe de base.  
  
### Émetteurs d'événements  
 Tout objet capable de déclencher un événement est un *émetteur d'événements*, également appelé *source d'événements*.  Les formulaires, contrôles et objets définis par l'utilisateur sont des exemples d'émetteurs d'événements.  
  
### Gestionnaires d'événements  
 Les *gestionnaires d'événements* sont des procédures appelées lorsqu'un événement correspondant se produit.  Vous pouvez utiliser n'importe quelle sous\-routine valide avec une signature correspondante comme gestionnaire d'événements.  Il vous est cependant impossible d'utiliser une fonction en tant que gestionnaire d'événements parce qu'une fonction ne peut retourner une valeur à la source des événements.  
  
 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] utilise pour les gestionnaires d'événements une convention d'affectation de noms standard qui combine le nom de l'émetteur de l'événement, un trait de soulignement et le nom de l'événement.  Par exemple, l'événement `Click` d'un bouton appelé `button1` aurait pour nom `Sub button1_Click`.  
  
> [!NOTE]
>  Nous vous recommandons, mais ce n'est pas obligatoire, d'utiliser cette convention d'affectation de noms lorsque vous définissez des gestionnaires d'événements pour vos propres événements ; vous pouvez utiliser n'importe quel nom de sous\-routine valide.  
  
## Association d'événements aux gestionnaires d'événements  
 Avant de pouvoir utiliser un gestionnaire d'événements, vous devez au préalable l'associer à un événement à l'aide de l'instruction `Handles` ou `AddHandler`.  
  
### WithEvents et la clause Handles  
 L'instruction `WithEvents` et la clause `Handles` assurent une méthode déclarative de spécification des gestionnaires d'événements.  Un événement déclenché par un objet déclaré par le mot clé `WithEvents` peut être géré par n'importe quelle procédure avec une instruction `Handles` pour cet événement, comme le montre l'exemple suivant :  
  
 [!code-vb[VbVbalrEvents#1](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#1)]  
  
 L'instruction `WithEvents` et la clause `Handles` représentent souvent la meilleure solution pour les gestionnaires d'événements, parce que la syntaxe déclarative qu'ils utilisent simplifie beaucoup le codage, la lecture et le débogage de la gestion des événements.  Il faut cependant garder à l'esprit les restrictions liées à l'utilisation des variables `WithEvents` :  
  
-   Vous ne pouvez pas utiliser une variable `WithEvents` comme variable d'objet.  Cela signifie que vous ne pouvez pas la déclarer en tant que `Object` ; vous devez spécifier le nom de la classe lorsque vous déclarez la variable.  
  
-   Les événements partagés ``  n'étant pas associés à des instances de classe, vous ne pouvez pas utiliser `WithEvents` pour les gérer de façon déclarative.  De même, vous ne pouvez pas utiliser `WithEvents` ou `Handles` pour gérer les événements de `Structure`.  Dans les deux cas, vous pouvez utiliser l'instruction `AddHandler` pour gérer ces événements.  
  
-   Vous ne pouvez pas créer de tableaux de variables `WithEvents`.  
  
 Les variables `WithEvents` autorisent un seul gestionnaire d'événements à gérer un ou plusieurs types d'événements ou un ou plusieurs gestionnaires d'événements à gérer le même type d'événements.  
  
 Même si la clause `Handles` constitue la méthode standard d'association d'un événement à un gestionnaire d'événements, son action est restreinte à l'association d'événements aux gestionnaires d'événements au moment de la compilation.  
  
 Dans certains cas \(par exemple, avec des événements associés à des formulaires ou des contrôles\), [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] définit automatiquement un gestionnaire d'événements vide et l'associe à un événement.  Par exemple, lorsque vous double\-cliquez sur un bouton de commande dans un formulaire en mode design, [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] crée un gestionnaire d'événements vide et une variable `WithEvents` pour le bouton de commande, comme dans le code suivant :  
  
 [!code-vb[VbVbalrEvents#26](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#26)]  
  
### AddHandler et RemoveHandler  
 L'instruction `AddHandler` est comparable à la clause `Handles` dans la mesure où toutes deux vous permettent de spécifier un gestionnaire d'événements.  Cependant, `AddHandler` utilisé conjointement avec `RemoveHandler`, offre une plus grande souplesse que la clause `Handles` ; ils vous permettent d'ajouter, de supprimer et de changer dynamiquement le gestionnaire d'événements associé à un événement.  Si vous souhaitez gérer des événements partagés ou des événements d'une structure, vous devez utiliser `AddHandler`.  
  
 `AddHandler` prend en compte deux arguments : le nom d'un événement issu d'un émetteur d'événements tel qu'un contrôle et une expression qui a pour valeur un délégué.  Comme l'instruction `AddressOf` retourne toujours une référence au délégué, vous n'êtes pas obligé de spécifier explicitement la classe déléguée lorsque vous utilisez `AddHandler`.  L'exemple ci\-dessous associe un gestionnaire d'événements à un événement déclenché par un objet :  
  
 [!code-vb[VbVbalrEvents#28](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#28)]  
  
 `RemoveHandler`, qui déconnecte un événement d'un gestionnaire d'événements, utilise la même syntaxe que `AddHandler`.  Par exemple :  
  
 [!code-vb[VbVbalrEvents#29](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#29)]  
  
 Dans l'exemple suivant, un gestionnaire d'événements est associé à un événement et cet événement est déclenché.  Le gestionnaire d'événements intercepte l'événement et affiche un message.  
  
 Le premier gestionnaire d'événements est ensuite supprimé et un autre gestionnaire d'événements est associé à l'événement.  Lorsque l'événement est de nouveau déclenché, un autre message s'affiche.  
  
 Enfin, le second gestionnaire d'événements est supprimé et l'événement est déclenché pour la troisième fois.  Étant donné qu'aucun gestionnaire d'événements n'est désormais associé à l'événement, aucune action n'est effectuée.  
  
 [!code-vb[VbVbalrEvents#38](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class2.vb#38)]  
  
## Gestion d'événements hérités d'une classe de base  
 Les *Classes dérivées*, classes qui héritent des caractéristiques d'une classe de base, peuvent gérer des événements déclenchés par leur classe de base à l'aide de l'instruction `Handles` `MyBase`.  
  
#### Pour gérer les événements d'une classe de base  
  
-   Déclarez un gestionnaire d'événements dans la classe dérivée en ajoutant une instruction `Handles MyBase.`*NomÉvénement* à la ligne de déclaration de votre procédure gestionnaire d'événements, où *NomÉvénement* est le nom de l'événement dans la classe de base gérée.  Par exemple :  
  
     [!code-vb[VbVbalrEvents#12](../../../../visual-basic/language-reference/statements/codesnippet/visualbasic/VbVbalrEvents/Class1.vb#12)]  
  
## Rubriques connexes  
  
|Titre|Description|  
|-----------|-----------------|  
|[Walkthrough: Declaring and Raising Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-declaring-and-raising-events.md)|Fournit une description pas à pas de la déclaration et du déclenchement des événements pour une classe.|  
|[Walkthrough: Handling Events](../../../../visual-basic/programming-guide/language-features/events/walkthrough-handling-events.md)|Montre comment écrire une procédure gestionnaire d'événements.|  
|[How to: Declare Custom Events To Avoid Blocking](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)|Montre comment définir un événement personnalisé qui autorise l'appel asynchrone de ses gestionnaires d'événements.|  
|[How to: Declare Custom Events To Conserve Memory](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-conserve-memory.md)|Montre comment définir un événement personnalisé qui utilise la mémoire uniquement lorsque l'événement est géré.|  
|[Troubleshooting Inherited Event Handlers in Visual Basic](../../../../visual-basic/programming-guide/language-features/events/troubleshooting-inherited-event-handlers.md)|Répertorie les problèmes courants liés aux gestionnaires d'événements dans les composants hérités.|  
|[Événements](../Topic/Handling%20and%20Raising%20Events.md)|Propose une vue d'ensemble du modèle d'événement dans le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort-md.md)].|  
|[Création de gestionnaires d'événements dans les Windows Forms](../Topic/Creating%20Event%20Handlers%20in%20Windows%20Forms.md)|Décrit comment utiliser des événements associés aux objets Windows Forms.|  
|[Delegates](../../../../visual-basic/programming-guide/language-features/delegates/delegates.md)|Fournit une vue d'ensemble de délégués dans Visual Basic.|
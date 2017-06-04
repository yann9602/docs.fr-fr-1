---
title: "Impl&#233;mentation d&#39;une m&#233;thode Dispose | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Dispose (méthode)"
  - "le garbage collection, la méthode Dispose"
ms.assetid: eb4e1af0-3b48-4fbc-ad4e-fc2f64138bf9
caps.latest.revision: 44
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 44
---
# Impl&#233;mentation d&#39;une m&#233;thode Dispose
Vous implémentez une méthode <xref:System.IDisposable.Dispose%2A> pour libérer les ressources non managées utilisées par votre application. Le récupérateur de mémoire du .NET Framework n’alloue ni ne libère de la mémoire non managée.  
  
 Le modèle pour supprimer un objet, appelé un [modèle de suppression](../../../docs/standard/design-guidelines/dispose-pattern.md), impose un ordre sur la durée de vie d’un objet. Le modèle de suppression est utilisé uniquement pour les objets qui accèdent à des ressources non managées, telles que les handles de fichiers et de canaux, les handles d’attente, les handles d’attente ou les pointeurs vers les blocs de mémoire non managée. Cela est dû au fait que le récupérateur de mémoire est très efficace pour récupérer les objets managés inutilisés, mais ne peut pas récupérer les objets non managés.  
  
 Le modèle de suppression comporte deux variantes :  
  
-   Vous encapsulez chaque ressource non managée utilisée par un type dans un handle sécurisé (autrement dit, dans une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName>). Dans ce cas, vous implémentez l’interface <xref:System.IDisposable> et une méthode `Dispose(Boolean)` supplémentaire. Il s’agit de la variante recommandée. Elle ne requiert pas le remplacement de la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
    > [!NOTE]
    >  L’espace de noms <xref:Microsoft.Win32.SafeHandles?displayProperty=fullName> fournit un ensemble de classes dérivées de <xref:System.Runtime.InteropServices.SafeHandle>, qui sont répertoriées dans la section [Utilisation des handles sécurisés](#SafeHandles). Si vous ne parvenez pas à trouver une classe qui convient pour libérer votre ressource non managée, vous pouvez implémenter votre propre sous-classe de <xref:System.Runtime.InteropServices.SafeHandle>.  
  
-   Vous implémentez la <xref:System.IDisposable> interface et une autre `Dispose(Boolean)` (méthode), puis vous remplacez le <xref:System.Object.Finalize%2A?displayProperty=fullName> méthode. Vous devez remplacer <xref:System.Object.Finalize%2A> pour garantir que les ressources non managées sont supprimées si votre implémentation de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> n’est pas appelée par un consommateur de votre type. Si vous utilisez la technique recommandée présentée dans le point précédent, la classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> effectue cette opération en votre nom.  
  
 Pour garantir que les ressources sont toujours correctement nettoyées, une méthode <xref:System.IDisposable.Dispose%2A> doit pouvoir être appelée à plusieurs reprises sans lever d’exception.  
  
> [!IMPORTANT]
>  Si vous êtes un programmeur C++, n’implémentez pas la <xref:System.IDisposable.Dispose%2A> méthode. Au lieu de cela, suivez les instructions de la section « Destructeurs et finaliseurs » de [Comment : définir et consommer des Classes et des Structs (C + c++ / CLI)](../Topic/How%20to:%20Define%20and%20Consume%20Classes%20and%20Structs%20\(C++-CLI\).md). À compter de .NET Framework 2.0, le compilateur C++ prend en charge la suppression déterminable de ressources et n’autorise pas l’implémentation directe de la <xref:System.IDisposable.Dispose%2A> méthode.  
  
 L’exemple de code fourni pour la méthode <xref:System.GC.KeepAlive%2A?displayProperty=fullName> affiche la façon dont un garbage collection agressif peut entraîner l’exécution d’un finaliseur pendant qu’un membre de l’objet demandé est toujours en cours d’exécution. Il est judicieux d’appeler le <xref:System.GC.KeepAlive%2A> méthode à la fin d’une longue <xref:System.IDisposable.Dispose%2A> méthode.  
  
<a name="Dispose2"></a>   
## <a name="dispose-and-disposeboolean"></a>Dispose() et Dispose(Boolean)  
 L’interface <xref:System.IDisposable> exige l’implémentation d’une méthode unique sans paramètre, <xref:System.IDisposable.Dispose%2A>. Toutefois, le modèle de suppression requiert deux méthodes `Dispose` à implémenter :  
  
-   Implémentation non virtuelle publique de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> (`NonInheritable` en Visual Basic) qui n’a aucun paramètre.  
  
-   Méthode virtuelle (`Overridable` en Visual Basic) `Dispose` dont la signature est :  
  
     [!code-csharp[Conceptual.Disposable#8](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#8)]
     [!code-vb[Conceptual.Disposable#8](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#8)]  
  
### <a name="the-dispose-overload"></a>Surcharge de Dispose()  
 Comme la méthode `NonInheritable` sans paramètre non virtuelle (`Dispose` en Visual Basic) publique est appelée par un consommateur de type, son objectif est de libérer les ressources non managées et d'indiquer que le finaliseur, s'il en existe un, ne doit pas s'exécuter. De ce fait, son implémentation standard est la suivante :  
  
 [!code-csharp[Conceptual.Disposable#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/dispose1.cs#7)]
 [!code-vb[Conceptual.Disposable#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/dispose1.vb#7)]  
  
 La méthode `Dispose` effectue le nettoyage de tous les objets. Le Garbage collector n’a plus donc besoin d’appeler la substitution <xref:System.Object.Finalize%2A?displayProperty=fullName>des objets. Par conséquent, l’appel à la <xref:System.GC.SuppressFinalize%2A> méthode empêche le garbage collector de l’exécution du finaliseur. Si le type n’a aucun finaliseur, l’appel à <xref:System.GC.SuppressFinalize%2A?displayProperty=fullName> n’a aucun effet. Notez que le travail réel de libération des ressources non managées est effectué par la deuxième surcharge de la méthode `Dispose`.  
  
### <a name="the-disposeboolean-overload"></a>Surcharge de Dispose(Boolean)  
 Dans la seconde surcharge, le `disposing` le paramètre est un <xref:System.Boolean> qui indique si l’appel de méthode provient d’un <xref:System.IDisposable.Dispose%2A> (méthode) (sa valeur est `true`) ou d’un finaliseur (sa valeur est `false`).  
  
 Le corps de la méthode se compose de deux blocs de code :  
  
-   Un bloc qui libère les ressources non managées. Ce bloc s'exécute indépendamment de la valeur du paramètre `disposing`.  
  
-   Un bloc conditionnel qui libère les ressources managées. Ce bloc s'exécute si la valeur de `disposing` est `true`. Les ressources managées qu'il libère peuvent inclure :  
  
     **Objets managés qui implémentent <xref:System.IDisposable>.**  
     Le bloc conditionnel peut être utilisé pour appeler leur implémentation de <xref:System.IDisposable.Dispose%2A>. Si vous avez utilisé un handle sécurisé pour encapsuler votre ressource non managée, vous devez appeler le <xref:System.Runtime.InteropServices.SafeHandle.Dispose%28System.Boolean%29?displayProperty=fullName> implémentation ici.  
  
     **Objets managés qui consomment de grandes quantités de mémoire ou consomment des ressources rares.**  
     La libération de ces objets explicitement dans la méthode `Dispose` les libère plus rapidement que s'ils ont été récupérés de façon non déterministe par le récupérateur de mémoire.  
  
 Si l'appel de la méthode vient d'un finaliseur (autrement dit, si `disposing` est `false`), seul le code qui libère les ressources non managées s'exécute. Étant donné que l'ordre dans lequel le récupérateur de mémoire détruit les objets managés pendant la finalisation n'est pas défini, l'appel de cette surcharge `Dispose` avec la valeur `false` empêche le finaliseur d'essayer de libérer les ressources managées qui peuvent avoir déjà été récupérées.  
  
## <a name="implementing-the-dispose-pattern-for-a-base-class"></a>Implémentation du modèle de suppression d'une classe de base  
 Si vous implémentez le modèle de suppression d’une classe de base, vous devez spécifier ce qui suit :  
  
> [!IMPORTANT]
>  Vous devez implémenter ce modèle pour toutes les classes de base qui implémentent <xref:System.IDisposable> et ne sont pas `sealed` (`NotInheritable` en Visual Basic).  
  
-   Une implémentation de <xref:System.IDisposable.Dispose%2A> qui appelle la méthode `Dispose(Boolean)`.  
  
-   Une méthode `Dispose(Boolean)` qui effectue le travail réel de libération des ressources.  
  
-   Une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName>. La classe <xref:System.Runtime.InteropServices.SafeHandle>fournit un finaliseur qui vous permet de ne pas avoir à en coder un.  
  
 Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui utilise un handle sécurisé.  
  
 [!code-csharp[System.IDisposable#3](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base1.cs#3)]
 [!code-vb[System.IDisposable#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base1.vb#3)]  
  
> [!NOTE]
>  L’exemple précédent utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour illustrer le modèle, mais il est possible d’utiliser à la place n’importe quel objet dérivé de <xref:System.Runtime.InteropServices.SafeHandle>. Notez que l’exemple n’instancie pas correctement son objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
 Voici le modèle général d’implémentation du modèle de suppression d’une classe de base qui remplace <xref:System.Object.Finalize%2A?displayProperty=fullName>.  
  
 [!code-csharp[System.IDisposable#5](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/base2.cs#5)]
 [!code-vb[System.IDisposable#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/base2.vb#5)]  
  
> [!NOTE]
>  En c#, vous substituez <xref:System.Object.Finalize%2A?displayProperty=fullName> en définissant un [destructeur](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md).  
  
## <a name="implementing-the-dispose-pattern-for-a-derived-class"></a>Implémentation du modèle de suppression d’une classe dérivée  
 Une classe dérivée d’une classe qui implémente l’interface <xref:System.IDisposable> ne doit pas implémenter <xref:System.IDisposable>, car l’implémentation de la classe de base de <xref:System.IDisposable.Dispose%2A?displayProperty=fullName> est héritée par ses classes dérivées. À la place, pour implémenter le modèle de suppression d’une classe dérivée, vous fournissez ce qui suit :  
  
-   Une méthode `protected``Dispose(Boolean)` qui substitue la méthode de la classe de base et effectue le travail réel de libération des ressources de la classe dérivée. Cette méthode doit également appeler la méthode `Dispose(Boolean)` de la classe de base et lui passer une valeur `true` pour l'argument `disposing`.  
  
-   Une classe dérivée de <xref:System.Runtime.InteropServices.SafeHandle> qui encapsule votre ressource managée (recommandée) ou une substitution de la méthode <xref:System.Object.Finalize%2A?displayProperty=fullName>. La classe <xref:System.Runtime.InteropServices.SafeHandle>fournit un finaliseur qui vous permet de ne pas avoir à en coder un. Si vous fournissez un finaliseur, il doit appeler la surcharge `Dispose(Boolean)` avec un argument égal à `disposing` `false`.  
  
 Voici le modèle général d’implémentation du modèle de suppression d’une classe dérivée qui utilise un handle sécurisé :  
  
 [!code-csharp[System.IDisposable#4](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived1.cs#4)]
 [!code-vb[System.IDisposable#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived1.vb#4)]  
  
> [!NOTE]
>  L’exemple précédent utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour illustrer le modèle, mais il est possible d’utiliser à la place n’importe quel objet dérivé de <xref:System.Runtime.InteropServices.SafeHandle>. Notez que l’exemple n’instancie pas correctement son objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>.  
  
 Voici le modèle général d’implémentation du modèle de suppression d’une classe dérivée qui remplace <xref:System.Object.Finalize%2A?displayProperty=fullName> :  
  
 [!code-csharp[System.IDisposable#6](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.idisposable/cs/derived2.cs#6)]
 [!code-vb[System.IDisposable#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.idisposable/vb/derived2.vb#6)]  
  
> [!NOTE]
>  En c#, vous substituez <xref:System.Object.Finalize%2A?displayProperty=fullName> en définissant un [destructeur](../Topic/Destructors%20\(C%23%20Programming%20Guide\).md).  
  
<a name="SafeHandles"></a>   
## <a name="using-safe-handles"></a>Utilisation des handles sécurisés  
 L’écriture de code pour le finaliseur d’un objet est une tâche complexe qui peut provoquer des problèmes si elle n’est pas effectuée correctement. Par conséquent, nous vous recommandons de construire des objets <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> au lieu d’implémenter un finaliseur.  
  
 Les classes dérivées de la classe <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName> simplifient les problèmes de durée de vie des objets en assignant et en libérant des handles sans interruption. Elles contiennent un finaliseur critique dont le fonctionnement pendant le déchargement d'un domaine d'application est garanti. Pour plus d’informations sur les avantages de l’utilisation d’un handle sécurisé, consultez <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName>. Les classes dérivées suivantes de l’espace de noms <xref:Microsoft.Win32.SafeHandles> fournissent des handles sécurisés :  
  
-   La classe <xref:Microsoft.Win32.SafeHandles.SafeFileHandle>, <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedFileHandle> et <xref:Microsoft.Win32.SafeHandles.SafePipeHandle>, pour les fichiers, les fichiers mappés en mémoire et les canaux.  
  
-   La classe <xref:Microsoft.Win32.SafeHandles.SafeMemoryMappedViewHandle>, pour les vues de la mémoire.  
  
-   Les classes <xref:Microsoft.Win32.SafeHandles.SafeNCryptKeyHandle>, <xref:Microsoft.Win32.SafeHandles.SafeNCryptProviderHandle> et <xref:Microsoft.Win32.SafeHandles.SafeNCryptSecretHandle>, pour les constructions de chiffrement.  
  
-   La classe <xref:Microsoft.Win32.SafeHandles.SafeRegistryHandle>, pour les clés de Registre.  
  
-   La classe <xref:Microsoft.Win32.SafeHandles.SafeWaitHandle>, pour les handles d’attente.  
  
<a name="base"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-base-class"></a>Utilisation d’un handle sécurisé pour implémenter le modèle de suppression d’une classe de base  
 L'exemple suivant illustre le modèle de suppression d'une classe de base, `DisposableStreamResource`, qui utilise un handle sécurisé pour encapsuler les ressources non managées. Il définit une classe `DisposableResource`qui utilise un <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour encapsuler un objet <xref:System.IO.Stream> qui représente un fichier ouvert. La méthode `DisposableResource` inclut également une seule propriété, `Size`, qui retourne le nombre total d'octets du flux de fichier.  
  
 [!code-csharp[Conceptual.Disposable#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/base1.cs#9)]
 [!code-vb[Conceptual.Disposable#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/base1.vb#9)]  
  
<a name="derived"></a>   
## <a name="using-a-safe-handle-to-implement-the-dispose-pattern-for-a-derived-class"></a>Utilisation d'un handle sécurisé pour implémenter le modèle de suppression d'une classe dérivée  
 L'exemple suivant illustre le modèle de suppression d'une classe dérivée, `DisposableStreamResource2`, qui hérite de la classe `DisposableStreamResource` présentée dans l'exemple précédent. La classe ajoute une méthode supplémentaire, `WriteFileInfo`, et utilise un objet <xref:Microsoft.Win32.SafeHandles.SafeFileHandle> pour encapsuler le handle du fichier accessible en écriture.  
  
 [!code-csharp[Conceptual.Disposable#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.disposable/cs/derived1.cs#10)]
 [!code-vb[Conceptual.Disposable#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.disposable/vb/derived1.vb#10)]  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.GC.SuppressFinalize%2A>   
 <xref:System.IDisposable>   
 <xref:System.IDisposable.Dispose%2A?displayProperty=fullName>   
 <xref:Microsoft.Win32.SafeHandles>   
 <xref:System.Runtime.InteropServices.SafeHandle?displayProperty=fullName>   
 <xref:System.Object.Finalize%2A?displayProperty=fullName>   
 [Comment : définir et consommer des Classes et Structs (C + c++ / CLI)](../Topic/How%20to:%20Define%20and%20Consume%20Classes%20and%20Structs%20\(C++-CLI\).md)   
 [Modèle de suppression](../../../docs/standard/design-guidelines/dispose-pattern.md)
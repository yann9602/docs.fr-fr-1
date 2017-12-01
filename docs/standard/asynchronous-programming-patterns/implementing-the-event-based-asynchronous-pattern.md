---
title: "Implémentation du modèle asynchrone basé sur des événements"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Event-based Asynchronous Pattern
- ProgressChangedEventArgs class
- BackgroundWorker component
- events [.NET Framework], asynchronous
- Asynchronous Pattern
- AsyncOperationManager class
- threading [.NET Framework], asynchronous features
- components [.NET Framework], asynchronous
- AsyncOperation class
- AsyncCompletedEventArgs class
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b4df5e4df914d932c7413e9330e8663753456c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="implementing-the-event-based-asynchronous-pattern"></a>Implémentation du modèle asynchrone basé sur des événements
Si vous écrivez une classe avec certaines opérations pouvant entraîner d’importants retards, pensez à lui affecter des fonctionnalités asynchrones en implémentant [Vue d’ensemble du modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Le modèle asynchrone basé sur des événements fournit une méthode standardisée pour empaqueter une classe incluant des fonctionnalités asynchrones. Si implémenté avec des classes d’assistance telles que <xref:System.ComponentModel.AsyncOperationManager>, votre classe fonctionnera correctement sous tout modèle d’application, y compris [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], des applications Windows Forms et des applications Console.  
  
 Pour obtenir un exemple qui implémente le modèle asynchrone basé sur des événements, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Pour les opérations asynchrones simples, vous trouverez peut-être la <xref:System.ComponentModel.BackgroundWorker> composant approprié. Pour plus d’informations sur <xref:System.ComponentModel.BackgroundWorker>, consultez [Comment : exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 La liste suivante décrit les fonctionnalités du modèle asynchrone basé sur des événements décrites dans cette rubrique.  
  
-   Possibilités d’implémentation du modèle asynchrone basé sur des événements  
  
-   Attribution des noms de méthodes asynchrones  
  
-   Annulation facultative de prise en charge  
  
-   Prise en charge facultative de la propriété IsBusy  
  
-   Prise en charge facultative du rapport de progression  
  
-   Prise en charge facultative du renvoi des résultats incrémentiels  
  
-   Gestion des paramètres Out et Ref dans les méthodes  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Possibilités d’implémentation du modèle asynchrone basé sur des événements  
 Envisagez d’implémenter le modèle asynchrone basé sur des événements quand :  
  
-   Les clients de votre classe n’est pas nécessitent <xref:System.Threading.WaitHandle> et <xref:System.IAsyncResult> objets disponibles pour les opérations asynchrones, ce qui signifie que l’interrogation et <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> devrez être développés par le client.  
  
-   Vous souhaitez que les opérations asynchrones soient gérées par le client avec le modèle d’événement/de délégué familier.  
  
 Une opération est un candidat pour une implémentation asynchrone, mais vous devez prendre en compte celles impliquant des latences importantes. Les opérations tout particulièrement appropriées sont celles dans lesquelles les clients appellent une méthode et sont informés de l’achèvement, sans autre intervention nécessaire. Sont également appropriées des opérations exécutées en continu et qui informent régulièrement les clients de la progression, des résultats incrémentiels ou des changements d’état.  
  
 Pour plus d’informations sur le choix du moment auquel prendre en charge le modèle asynchrone basé sur des événements, consultez [Choix du moment auquel implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Attribution des noms de méthodes asynchrones  
 Pour chaque méthode synchrone *MethodName* pour laquelle vous souhaitez fournir un équivalent asynchrone :  
  
 Définissez une méthode *MethodName*`Async` qui :  
  
-   Retourne `void`.  
  
-   Accepte les mêmes paramètres que la méthode *MethodName*.  
  
-   Accepte plusieurs appels.  
  
 Définissez éventuellement une surcharge *MethodName*`Async`, identique à *MethodName*`Async`, mais avec un paramètre objet supplémentaire appelé `userState`. Procédez ainsi si vous êtes prêt à gérer plusieurs appels simultanés de votre méthode, auquel cas la valeur `userState` est remise à tous les gestionnaires d’événements pour distinguer les appels de la méthode. Vous pouvez également choisir d’en faire un emplacement de stockage de l’état utilisateur pour une récupération ultérieure.  
  
 Pour chaque signature de méthode distincte pour *MethodName*`Async` :  
  
1.  Définissez l’événement suivant dans la même classe que la méthode :  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Définissez le délégué suivant et <xref:System.ComponentModel.AsyncCompletedEventArgs>. Ils seront probablement définis en dehors de la classe, mais dans le même espace de noms.  
  
    ```vb  
    Public Delegate Sub MethodNameCompletedEventHandler( _  
        ByVal sender As Object, _  
        ByVal e As MethodNameCompletedEventArgs)  
  
    Public Class MethodNameCompletedEventArgs  
        Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As MyReturnType  
    End Property  
    ```  
  
    ```csharp  
    public delegate void MethodNameCompletedEventHandler(object sender,   
        MethodNameCompletedEventArgs e);  
  
    public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
    {  
        public MyReturnType Result { get; }  
    }  
    ```  
  
    -   Assurez-vous que la classe *MethodName*`CompletedEventArgs` expose ses membres en tant que propriétés en lecture seule et non en tant que champs, car les champs empêchent la liaison des données.  
  
    -   Ne définissez aucune <xref:System.ComponentModel.AsyncCompletedEventArgs>-dérivées des classes pour les méthodes qui ne produisent pas de résultats. Utilisez simplement une instance de <xref:System.ComponentModel.AsyncCompletedEventArgs> lui-même.  
  
        > [!NOTE]
        >  Il est parfaitement acceptable, lorsque cela est possible et approprié, de réutiliser le délégué et <xref:System.ComponentModel.AsyncCompletedEventArgs> types. Dans ce cas, l’attribution de noms pas sera aussi cohérente avec le nom de la méthode, depuis un délégué donné et <xref:System.ComponentModel.AsyncCompletedEventArgs> ne seront pas liés à une méthode unique.  
  
## <a name="optionally-support-cancellation"></a>Annulation facultative de prise en charge  
 Si votre classe prend en charge l’annulation des opérations asynchrones, l’annulation doit être présentée au client comme décrit ci-dessous. Notez que deux décisions importantes doivent être prises avant de définir l’annulation de la prise en charge :  
  
-   Votre classe, y compris ses ajouts futurs, comprend-elle une seule opération asynchrone prenant en charge l’annulation ?  
  
-   Les opérations asynchrones prenant en charge l’annulation de prise en charge peuvent-elles prendre en charge plusieurs opérations en attente ? Autrement dit, la méthode *MethodName*`Async` accepte-t-elle un paramètre `userState` et autorise-t-elle les appels multiples avant d’attendre que l’un d’eux se termine ?  
  
 Utilisez les réponses à ces deux questions dans le tableau ci-dessous pour déterminer la signature de votre méthode d’annulation.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Plusieurs opérations simultanées prises en charge|Une seule opération à la fois|  
|------|------------------------------------------------|----------------------------------|  
|Une opération Async dans la classe entière|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Plusieurs opérations Async dans la classe|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Plusieurs opérations simultanées prises en charge|Une seule opération à la fois|  
|------|------------------------------------------------|----------------------------------|  
|Une opération Async dans la classe entière|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Plusieurs opérations Async dans la classe|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Si vous définissez la méthode `CancelAsync(object userState)`, les clients doivent être prudents lorsqu’ils choisissent leurs valeurs d’état afin qu’elles soient capables de distinguer toutes les méthodes asynchrones appelées sur l’objet, et pas seulement tous les appels d’une seule méthode asynchrone.  
  
 La décision de nommer la version de l’opération asynchrone simple *MethodName*`AsyncCancel` est motivée par la capacité à découvrir plus facilement la méthode dans un environnement de conception comme IntelliSense de Visual Studio. Il regroupe les membres associés et les distingue des autres membres qui n’ont rien à voir avec les fonctionnalités asynchrones. Si vous pensez que d’autres opérations asynchrones peuvent être ajoutées dans les versions ultérieures, il est préférable de définir `CancelAsync`.  
  
 Ne définissez pas plusieurs méthodes du tableau ci-dessus dans la même classe. Ceci sera inutile ou risquera d’encombrer l’interface de classe d’un trop grand nombre de méthodes.  
  
 Ces méthodes retournent généralement immédiatement et l’opération peut ou non être réellement annulée. Dans le gestionnaire d’événements de l’événement *MethodName*`Completed`, l’objet *MethodName*`CompletedEventArgs` contient un champ `Cancelled` que les clients peuvent utiliser pour déterminer si l’annulation a eu lieu.  
  
 Respectez la sémantique d’annulation décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Prise en charge facultative de la propriété IsBusy  
 Si votre classe ne prend pas en charge plusieurs appels simultanés, envisagez d’exposer une propriété `IsBusy`. Cela permet aux développeurs de déterminer si une méthode *MethodName*`Async` s’exécute sans intercepter d’exception de la méthode *MethodName*`Async`.  
  
 Respectez la sémantique `IsBusy` décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Prise en charge facultative du rapport de progression  
 Il est généralement souhaitable qu’une opération asynchrone indique sa progression pendant son fonctionnement. Le modèle asynchrone basé sur des événements fournit des instructions pour le faire.  
  
-   Définissez éventuellement un événement déclenché par l’opération asynchrone et appelé sur le thread approprié. Le <xref:System.ComponentModel.ProgressChangedEventArgs> objet comporte un indicateur de progression de valeurs entières qui doit être comprise entre 0 et 100.  
  
-   Nommez cet événement de la façon suivante :  
  
    -   `ProgressChanged` si la classe comporte plusieurs opérations asynchrones (ou est censée se développer pour inclure plusieurs opérations asynchrones dans les versions ultérieures) ;  
  
    -   *MethodName* `ProgressChanged` si la classe comporte une seule opération asynchrone.  
  
     Ce choix de désignation correspond à celui effectué pour la méthode d’annulation, comme décrit dans la section Annulation facultative de la prise en charge.  
  
 Cet événement doit utiliser la <xref:System.ComponentModel.ProgressChangedEventHandler> signature du délégué et la <xref:System.ComponentModel.ProgressChangedEventArgs> classe. Vous pouvez également, si un indicateur de progression plus spécifique au domaine peut être fourni (par instance, les octets lus et nombre total d’octets pour une opération de téléchargement), vous devez définir une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Notez qu’il existe un seul événement `ProgressChanged` ou *MethodName*`ProgressChanged` pour la classe, quel que soit le nombre de méthodes asynchrones qu’elle prend en charge. Les clients sont censés utiliser l’objet `userState` qui est passé aux méthodes *MethodName*`Async` pour distinguer les mises à jour de progression sur les opérations simultanées multiples.  
  
 Dans certaines situations, plusieurs opérations prennent en charge la progression et chacune renvoie un indicateur de progression différent. Dans ce cas, un seul événement `ProgressChanged` n’est pas approprié, et vous pouvez envisager la prise en charge de plusieurs événements `ProgressChanged`. Utilisez dans ce cas un modèle de nom *MethodName*`ProgressChanged` pour chaque méthode *MethodName*`Async`.  
  
 Respectez la sémantique de rapport de progression décrite dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Prise en charge facultative du renvoi des résultats incrémentiels  
 Parfois, une opération asynchrone peut retourner des résultats incrémentiels avant la fin. Un certain nombre d’options peuvent être utilisées pour prendre en charge ce scénario. En voici quelques exemples.  
  
### <a name="single-operation-class"></a>Classe à une opération  
 Si votre classe ne prend en charge qu’une seule opération asynchrone et que celle-ci peut retourner des résultats incrémentiels :  
  
-   Étendre la <xref:System.ComponentModel.ProgressChangedEventArgs> tapez pour intégrer les données de résultat incrémentiel et définissez un *MethodName* `ProgressChanged` événements avec ces données étendues.  
  
-   Déclenchez cet événement *MethodName*`ProgressChanged` lorsqu’un résultat incrémentiel doit être signalé.  
  
 Cette solution s’applique tout particulièrement à une classe d’opération asynchrone simple, car le fait que le même événement retourne des résultats incrémentiels sur « toutes les opérations », comme c’est le cas pour l’événement *MethodName*`ProgressChanged`, ne pose aucun problème.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Classe à plusieurs opérations avec des résultats incrémentiels homogènes  
 Dans ce cas, votre classe prend en charge plusieurs méthodes asynchrones, chacune capable de retourner des résultats incrémentiels, et ces résultats incrémentiels possèdent tous le même type de données.  
  
 Suivre le modèle décrit ci-dessus pour les classes de l’opération simple, comme le même <xref:System.EventArgs> structure fonctionne pour tous les résultats incrémentiels. Définissez un événement `ProgressChanged` à la place d’un événement *MethodName*`ProgressChanged` étant donné qu’il s’applique à plusieurs méthodes asynchrones.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Classe à plusieurs opérations avec des résultats incrémentiels hétérogènes  
 Si votre classe prend en charge plusieurs méthodes asynchrones, chacune retournant un type de données différent :  
  
-   Séparez votre rapport de résultat incrémentiel de votre rapport de progression.  
  
-   Définir un distinct *MethodName* `ProgressChanged` événement avec approprié <xref:System.EventArgs> pour chaque méthode asynchrone gérer les données de résultat incrémentiel de cette méthode.  
  
 Appelez ce gestionnaire d’événements sur le thread approprié comme décrit dans [Meilleures pratiques pour implémenter le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Gestion des paramètres Out et Ref dans les méthodes  
 Bien que l’utilisation de `out` et `ref` soit en règle générale déconseillée dans le .NET Framework, voici les règles à suivre lorsqu’ils sont présents :  
  
 Soit une méthode synchrone *MethodName* :  
  
-   Les paramètres `out` passés à *MethodName* ne doivent pas faire partie de *MethodName*`Async`. Ils doivent plutôt faire partie de *MethodName*`CompletedEventArgs` avec le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).  
  
-   Les paramètres `ref` passés à *MethodName* doivent faire partie de *MethodName*`Async`, et faire partie de *MethodName*`CompletedEventArgs` avec le même nom que son paramètre équivalent dans *MethodName* (à moins qu’il n’existe un nom plus approprié).  
  
 Par exemple, soit :  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Votre méthode asynchrone et sa <xref:System.ComponentModel.AsyncCompletedEventArgs> classe ressemble à ceci :  
  
```vb  
Public Sub MethodNameAsync(ByVal arg1 As String, ByVal arg2 As String)  
  
Public Class MethodNameCompletedEventArgs  
    Inherits System.ComponentModel.AsyncCompletedEventArgs  
    Public ReadOnly Property Result() As Integer   
    End Property  
    Public ReadOnly Property Arg2() As String   
    End Property  
    Public ReadOnly Property Arg3() As String   
    End Property  
End Class  
```  
  
```csharp  
public void MethodNameAsync(string arg1, string arg2);  
  
public class MethodNameCompletedEventArgs : System.ComponentModel.AsyncCompletedEventArgs  
{  
    public int Result { get; };  
    public string Arg2 { get; };  
    public string Arg3 { get; };  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.ComponentModel.ProgressChangedEventArgs>  
 <xref:System.ComponentModel.AsyncCompletedEventArgs>  
 [Guide pratique pour implémenter un composant qui prend en charge le modèle asynchrone basé sur des événements](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)  
 [Guide pratique pour exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [Choix du moment auquel implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)  
 [Programmation multithread avec le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)  
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur les événements](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)

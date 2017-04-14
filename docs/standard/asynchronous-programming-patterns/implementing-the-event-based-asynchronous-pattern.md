---
title: "Impl&#233;mentation du mod&#232;le asynchrone bas&#233; sur des &#233;v&#233;nements | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèle asynchrone basé sur les événements"
  - "ProgressChangedEventArgs (classe)"
  - "BackgroundWorker (composant)"
  - "événements (.NET Framework), asynchrones"
  - "modèle asynchrone"
  - "AsyncOperationManager (classe)"
  - "threads (.NET Framework), fonctionnalités asynchrones"
  - "composants (.NET Framework), asynchrones"
  - "AsyncOperation (classe)"
  - "AsyncCompletedEventArgs (classe)"
ms.assetid: 43402d19-8d30-426d-8785-1a4478233bfa
caps.latest.revision: 20
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 20
---
# Impl&#233;mentation du mod&#232;le asynchrone bas&#233; sur des &#233;v&#233;nements
Si vous écrivez une classe avec certaines opérations pouvant entraîner d’importants retards, pensez à lui affecter des fonctionnalités asynchrones en implémentant [Event-based Asynchronous Pattern Overview](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).  
  
 Le modèle asynchrone basé sur événement fournit une méthode standardisée pour empaqueter une classe qui possède des fonctionnalités asynchrones. Si implémentée avec des classes d’assistance telles que <xref:System.ComponentModel.AsyncOperationManager>, votre classe fonctionnera correctement sous tout modèle d’application, y compris [!INCLUDE[vstecasp](../../../includes/vstecasp-md.md)], des applications Windows Forms et des applications Console.  
  
 Pour obtenir un exemple qui implémente le modèle asynchrone basé sur des événements, consultez [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md).  
  
 Pour les opérations asynchrones simples, vous trouverez peut-être la <xref:System.ComponentModel.BackgroundWorker> composant approprié. Pour plus d’informations sur <xref:System.ComponentModel.BackgroundWorker>, consultez [Comment : exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).  
  
 La liste suivante décrit les fonctionnalités du modèle asynchrone basé sur événement décrits dans cette rubrique.  
  
-   Possibilités d’implémentation du modèle asynchrone basé sur événement  
  
-   Nommer des méthodes asynchrones  
  
-   Vous pouvez également en charge l’annulation  
  
-   Vous pouvez également prendre en charge la propriété IsBusy  
  
-   Si vous le souhaitez prennent en charge le rapport de progression  
  
-   Vous pouvez également retourner des résultats incrémentiels prennent en charge  
  
-   Gestion Out et Ref des paramètres dans les méthodes  
  
## <a name="opportunities-for-implementing-the-event-based-asynchronous-pattern"></a>Possibilités d’implémentation du modèle asynchrone basé sur événement  
 Envisagez d’implémenter le modèle asynchrone basé sur événement lorsque :  
  
-   Les clients de votre classe ne nécessitent <xref:System.Threading.WaitHandle> et <xref:System.IAsyncResult> les objets disponibles pour les opérations asynchrones, ce qui signifie que l’interrogation et <xref:System.Threading.WaitHandle.WaitAll%2A> ou <xref:System.Threading.WaitHandle.WaitAny%2A> devez être développés par le client.  
  
-   Vous souhaitez que les opérations asynchrones devant être gérés par le client avec le modèle d’événement/de délégué familière.  
  
 Une opération est un candidat pour une implémentation asynchrone, mais les que latences prévues doivent être considérés. Particulièrement appropriées sont des opérations dans laquelle les clients appellent une méthode et sont avertis de l’achèvement, sans autre intervention nécessaire. Opérations qui s’exécutent en continu et informent périodiquement les clients de la progression, les résultats incrémentiels ou modifications d’état sont également appropriées.  
  
 Pour plus d’informations sur le choix du moment adéquat prendre en charge le modèle asynchrone basé sur événement, consultez la page [décider quand pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md).  
  
## <a name="naming-asynchronous-methods"></a>Nommer des méthodes asynchrones  
 Pour chaque méthode synchrone *MethodName* pour lequel vous souhaitez fournir un équivalent asynchrone :  
  
 Définir un *MethodName* `Async` méthode qui :  
  
-   Retourne `void`.  
  
-   Accepte les mêmes paramètres que la *MethodName* méthode.  
  
-   Accepte les appels multiples.  
  
 Vous pouvez également définir un *MethodName* `Async` surcharge, identique à *MethodName*`Async`, mais avec un paramètre objet supplémentaire appelé `userState`. Si vous êtes prêt à gérer plusieurs appels simultanés de votre méthode, auquel cas la `userState` valeur est remise à tous les gestionnaires d’événements pour distinguer les appels de la méthode. Vous pouvez également choisir de procéder simplement comme un emplacement pour stocker l’état utilisateur pour une récupération ultérieure.  
  
 Pour chaque distinct *MethodName* `Async` signature de méthode :  
  
1.  Définissez l’événement suivant dans la même classe que la méthode :  
  
    ```vb  
    Public Event MethodNameCompleted As MethodNameCompletedEventHandler  
    ```  
  
    ```csharp  
    public event MethodNameCompletedEventHandler MethodNameCompleted;  
    ```  
  
2.  Définissez le délégué suivant et <xref:System.ComponentModel.AsyncCompletedEventArgs>. Ils seront probablement définis en dehors de la classe elle-même, mais dans le même espace de noms.  
  
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
  
    -   Assurez-vous que le *MethodName* `CompletedEventArgs` classe expose ses membres en tant que propriétés en lecture seule et non par des champs, car les champs empêchent la liaison de données.  
  
    -   Ne définissez aucune <xref:System.ComponentModel.AsyncCompletedEventArgs>-dérivées des classes pour les méthodes qui ne produisent pas de résultats. Utilisez simplement une instance de <xref:System.ComponentModel.AsyncCompletedEventArgs> lui-même.  
  
        > [!NOTE]
        >  Il est parfaitement acceptable, lorsque cela est possible et approprié, de réutiliser le délégué et <xref:System.ComponentModel.AsyncCompletedEventArgs> types. Dans ce cas, l’attribution de noms pas sera aussi cohérente avec le nom de la méthode depuis un délégué donné et <xref:System.ComponentModel.AsyncCompletedEventArgs> ne seront pas liés à une seule méthode.  
  
## <a name="optionally-support-cancellation"></a>Vous pouvez également en charge l’annulation  
 Si votre classe prend en charge l’annulation des opérations asynchrones, l’annulation doit être exposée au client comme décrit ci-dessous. Notez qu’il n’y a deux points importants doivent être décidés avant de définir votre support d’annulation :  
  
-   Votre classe, y compris les ajouts anticipés, a-t-il qu’une opération asynchrone qui prend en charge l’annulation  
  
-   Peut les opérations asynchrones qui prennent en charge le support d’annulation plusieurs opérations en attente ? Ne le *MethodName* `Async` méthode prennent un `userState` paramètre, et n’autorise pas plusieurs appels avant d’attendre que les terminer ?  
  
 Utilisez les réponses à ces deux questions dans le tableau ci-dessous pour déterminer la signature de votre méthode d’annulation.  
  
### <a name="visual-basic"></a>Visual Basic  
  
||Plusieurs opérations simultanées prises en charge|Une seule opération à la fois|  
|------|------------------------------------------------|----------------------------------|  
|Une opération Async dans la classe entière|`Sub MethodNameAsyncCancel(ByVal userState As Object)`|`Sub MethodNameAsyncCancel()`|  
|Plusieurs opérations asynchrones dans la classe|`Sub CancelAsync(ByVal userState As Object)`|`Sub CancelAsync()`|  
  
### <a name="c"></a>C#  
  
||Plusieurs opérations simultanées prises en charge|Une seule opération à la fois|  
|------|------------------------------------------------|----------------------------------|  
|Une opération Async dans la classe entière|`void MethodNameAsyncCancel(object userState);`|`void MethodNameAsyncCancel();`|  
|Plusieurs opérations asynchrones dans la classe|`void CancelAsync(object userState);`|`void CancelAsync();`|  
  
 Si vous définissez la `CancelAsync(object userState)` (méthode), les clients doivent être prudents lorsqu’ils choisissent leurs valeurs d’état afin qu’elles soient capables de distinguer toutes les méthodes asynchrones appelées sur l’objet et pas seulement tous les appels d’une seule méthode asynchrone.  
  
 La décision de nommer la version de l’opération asynchrone simple *MethodName* `AsyncCancel` est basée sur la capacité à découvrir plus facilement la méthode dans un environnement de design comme IntelliSense de Visual Studio. Il regroupe les membres associés et les distingue des autres membres qui n’ont rien à voir avec les fonctionnalités asynchrones. Si vous pensez qu’il peut y avoir plus des opérations asynchrones ajoutées dans les versions ultérieures, il est préférable de définir `CancelAsync`.  
  
 Ne définissez pas plusieurs méthodes du tableau ci-dessus dans la même classe. Qui sera inutile ou risque d’encombrer l’interface de classe d’une prolifération de méthodes.  
  
 Ces méthodes généralement retournent immédiatement, et l’opération peut ou non être réellement annulée. Dans le Gestionnaire d’événements pour le *MethodName* `Completed` événement, le *MethodName* `CompletedEventArgs` objet contient un `Cancelled` champ, dont les clients peuvent utiliser pour déterminer si l’annulation s’est produite.  
  
 Respectez la sémantique d’annulation décrite dans [meilleures pratiques pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-support-the-isbusy-property"></a>Vous pouvez également prendre en charge la propriété IsBusy  
 Si votre classe ne prend pas en charge plusieurs appels simultanés, exposez une `IsBusy` propriété. Cela permet aux développeurs de déterminer si une *MethodName* `Async` s’exécute sans intercepter d’exception de la *MethodName* `Async` (méthode).  
  
 Respecter la `IsBusy` sémantique décrite dans [meilleures pratiques pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-progress-reporting"></a>Si vous le souhaitez prennent en charge le rapport de progression  
 Il est souvent souhaitable pour une opération asynchrone pour signaler la progression pendant son fonctionnement. Le modèle asynchrone basé sur événement fournit des indications pour le faire.  
  
-   Définissez éventuellement un événement déclenché par l’opération asynchrone et appelé sur le thread approprié. Le <xref:System.ComponentModel.ProgressChangedEventArgs> objet comporte un indicateur de progression de valeurs entières qui doit être comprise entre 0 et 100.  
  
-   Nommez cet événement comme suit :  
  
    -   `ProgressChanged`Si la classe possède plusieurs opérations asynchrones (ou est censée s’agrandir pour inclure plusieurs opérations asynchrones dans les versions ultérieures) ;  
  
    -   *MethodName* `ProgressChanged` si la classe possède une seule opération asynchrone.  
  
     Ce choix de désignation correspond à celui qui effectuées pour la méthode d’annulation, comme décrit dans la section éventuellement prise en charge l’annulation.  
  
 Cet événement doit utiliser la <xref:System.ComponentModel.ProgressChangedEventHandler> signature du délégué et le <xref:System.ComponentModel.ProgressChangedEventArgs> classe. Toutefois, si un indicateur de progression plus spécifique au domaine peut être fourni (par instance, les octets lus et nombre total d’octets pour une opération de téléchargement), vous devez définir une classe dérivée de <xref:System.ComponentModel.ProgressChangedEventArgs>.  
  
 Notez qu’il y en a qu’un seul `ProgressChanged` ou *MethodName* `ProgressChanged` événements pour la classe, quel que soit le nombre de méthodes asynchrones, il prend en charge. Les clients doivent utiliser le `userState` objet qui est passé à la *MethodName* `Async` méthodes pour distinguer les mises à jour de progression sur les opérations simultanées multiples.  
  
 Il peut arriver dans lequel plusieurs opérations prennent en charge la progression et chacune renvoie un indicateur différent pour la progression. Dans ce cas, un seul `ProgressChanged` événement n’est pas approprié, et vous pouvez envisager la prise en charge de plusieurs `ProgressChanged` événements. Dans ce cas utiliser un modèle d’affectation de *MethodName* `ProgressChanged` pour chaque *MethodName* `Async` (méthode).  
  
 Respectez la sémantique de rapport de progression décrite [meilleures pratiques pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="optionally-provide-support-for-returning-incremental-results"></a>Vous pouvez également retourner des résultats incrémentiels prennent en charge  
 Parfois, une opération asynchrone peut retourner des résultats incrémentiels avant la fin. Il existe un certain nombre d’options qui peut être utilisé pour prendre en charge ce scénario. Voici quelques exemples.  
  
### <a name="single-operation-class"></a>Classe d’opération simple  
 Si votre classe prend en charge uniquement une seule opération asynchrone, et elle est en mesure de retourner des résultats incrémentiels, puis :  
  
-   Étendre la <xref:System.ComponentModel.ProgressChangedEventArgs> tapez pour intégrer les données de résultat incrémentiel et définissez un *MethodName* `ProgressChanged` événements avec ces données étendues.  
  
-   Déclenchez cet *MethodName* `ProgressChanged` événement lorsqu’un résultat incrémentiel au rapport.  
  
 Cette solution s’applique spécifiquement à une classe d’opération asynchrone simple, car il n’existe aucun problème avec le même événement pour retourner des résultats incrémentiels sur « toutes les opérations », comme le *MethodName* `ProgressChanged` événement.  
  
### <a name="multiple-operation-class-with-homogeneous-incremental-results"></a>Classe à plusieurs opérations avec des résultats incrémentiels homogènes  
 Dans ce cas, votre classe prend en charge plusieurs méthodes asynchrones, chacune capables de retourner des résultats incrémentiels, et ces résultats incrémentiels possèdent tous le même type de données.  
  
 Suivre le modèle décrit ci-dessus pour les classes de l’opération simple, comme le même <xref:System.EventArgs> structure fonctionne pour tous les résultats incrémentiels. Définir un `ProgressChanged` événements au lieu d’un *MethodName* `ProgressChanged` événement, dans la mesure où elle s’applique à plusieurs méthodes asynchrones.  
  
### <a name="multiple-operation-class-with-heterogeneous-incremental-results"></a>Classe à plusieurs opérations avec des résultats incrémentiels hétérogènes  
 Si votre classe prend en charge plusieurs méthodes asynchrones, chacune retournant un autre type de données, vous devez :  
  
-   Séparez votre résultat incrémentiel de votre rapport de progression.  
  
-   Définir un distinct *MethodName* `ProgressChanged` événement appropriée <xref:System.EventArgs> pour chaque méthode asynchrone gère les données de résultat incrémentiel de cette méthode.  
  
 Appeler ce gestionnaire d’événements sur le thread approprié comme décrit dans [meilleures pratiques pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md).  
  
## <a name="handling-out-and-ref-parameters-in-methods"></a>Gestion Out et Ref des paramètres dans les méthodes  
 Bien que l’utilisation de `out` et `ref` est, en règle générale, déconseillée dans le .NET Framework, voici les règles à suivre lorsqu’ils sont présents :  
  
 Selon une méthode synchrone *MethodName*:  
  
-   `out`paramètres *MethodName* ne doit pas faire partie de *MethodName*`Async`. Au lieu de cela, ils doivent faire partie de *MethodName* `CompletedEventArgs` portant le même nom que son paramètre équivalent dans *MethodName* (à moins qu’un nom plus approprié).  
  
-   `ref`paramètres *MethodName* doit apparaître dans le cadre de *MethodName*`Async`et dans le cadre de *MethodName* `CompletedEventArgs` portant le même nom que son paramètre équivalent dans *MethodName* (à moins qu’un nom plus approprié).  
  
 Par exemple, étant donné :  
  
```vb  
Public Function MethodName(ByVal arg1 As String, ByRef arg2 As String, ByRef arg3 As String) As Integer  
```  
  
```csharp  
public int MethodName(string arg1, ref string arg2, out string arg3);  
```  
  
 Votre méthode asynchrone et sa <xref:System.ComponentModel.AsyncCompletedEventArgs> classe ressemblerait à ceci :  
  
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
 [Comment : implémenter un composant qui prend en charge le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/component-that-supports-the-event-based-asynchronous-pattern.md)   
 [Comment : exécuter une opération en arrière-plan](../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)   
 [Comment : implémenter un formulaire qui utilise une opération d’arrière-plan](../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)   
 [Choix du moment auquel implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/deciding-when-to-implement-the-event-based-asynchronous-pattern.md)   
 [Programmation multithread avec le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/multithreaded-programming-with-the-event-based-asynchronous-pattern.md)   
 [Meilleures pratiques pour implémenter le modèle asynchrone basé sur événement](../../../docs/standard/asynchronous-programming-patterns/best-practices-for-implementing-the-event-based-asynchronous-pattern.md)
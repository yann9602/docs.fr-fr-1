---
title: "Modèles courants pour les délégués"
description: "Découvrez les modèles courants pour l’utilisation de délégués dans votre code afin d’éviter un couplage important entre vos composants."
keywords: .NET, .NET Core
author: BillWagner
ms.author: wiwagn
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: 0ff8fdfd-6a11-4327-b061-0f2526f35b43
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 83214800fb997e9274cacfd1bae85ab07c4515a2
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---

# <a name="common-patterns-for-delegates"></a><span data-ttu-id="3dd6a-104">Modèles courants pour les délégués</span><span class="sxs-lookup"><span data-stu-id="3dd6a-104">Common Patterns for Delegates</span></span>

[<span data-ttu-id="3dd6a-105">Précédent</span><span class="sxs-lookup"><span data-stu-id="3dd6a-105">Previous</span></span>](delegates-strongly-typed.md)

<span data-ttu-id="3dd6a-106">Les délégués fournissent un mécanisme qui autorise des conceptions logicielles impliquant un couplage minimal entre les composants.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-106">Delegates provide a mechanism that enables software designs involving minimal coupling between components.</span></span>

<span data-ttu-id="3dd6a-107">LINQ constitue un excellent exemple de ce genre de conception.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-107">One excellent example for this kind of design is LINQ.</span></span> <span data-ttu-id="3dd6a-108">Le modèle d’expression de requête LINQ s’appuie sur des délégués pour toutes ses fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-108">The LINQ Query Expression Pattern relies on delegates for all of its features.</span></span> <span data-ttu-id="3dd6a-109">Prenons l’exemple simple suivant :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-109">Consider this simple example:</span></span>

```csharp
var smallNumbers = numbers.Where(n => n < 10);
```

<span data-ttu-id="3dd6a-110">Il filtre la séquence de nombres pour ne sélectionner que ceux qui sont inférieurs à 10.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-110">This filters the sequence of numbers to only those less than the value 10.</span></span>
<span data-ttu-id="3dd6a-111">La méthode `Where` utilise un délégué qui détermine les éléments d’une séquence qui correspondent au filtre.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-111">The `Where` method uses a delegate that determines which elements of a sequence pass the filter.</span></span> <span data-ttu-id="3dd6a-112">Quand vous créez une requête LINQ, vous fournissez l’implémentation du délégué à cette fin spécifique.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-112">When you create a LINQ query, you supply the implementation of the delegate for this specific purpose.</span></span>

<span data-ttu-id="3dd6a-113">Le prototype de la méthode Where est le suivant :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-113">The prototype for the Where method is:</span></span>

```csharp
public static IEnumerable<TSource> Where<in TSource> (IEnumerable<TSource> source, Func<TSource, bool> predicate);
```

<span data-ttu-id="3dd6a-114">Cet exemple est répété avec toutes les méthodes qui font partie de LINQ.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-114">This example is repeated with all the methods that are part of LINQ.</span></span> <span data-ttu-id="3dd6a-115">Elles s’appuient toutes sur des délégués pour le code qui gère la requête spécifique.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-115">They all rely on delegates for the code that manages the specific query.</span></span> <span data-ttu-id="3dd6a-116">Ce modèle de conception d’API est très puissant, une fois appris et compris.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-116">This API design pattern is a very powerful one to learn and understand.</span></span>

<span data-ttu-id="3dd6a-117">Cet exemple simple montre que les délégués nécessitent très peu de couplage entre les composants.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-117">This simple example illustrates how delegates require very little coupling between components.</span></span> <span data-ttu-id="3dd6a-118">Vous n’avez pas besoin de créer de classe qui dérive d’une classe de base particulière.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-118">You don't need to create a class that derives from a particular base class.</span></span> <span data-ttu-id="3dd6a-119">Vous n’avez pas besoin d’implémenter une interface spécifique.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-119">You don't need to implement a specific interface.</span></span>
<span data-ttu-id="3dd6a-120">La seule exigence consiste à fournir l’implémentation d’une méthode qui est essentielle à la tâche en question.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-120">The only requirement is to provide the implementation of one method that is fundamental to the task at hand.</span></span>

## <a name="building-your-own-components-with-delegates"></a><span data-ttu-id="3dd6a-121">Création de vos propres composants avec des délégués</span><span class="sxs-lookup"><span data-stu-id="3dd6a-121">Building Your Own Components with Delegates</span></span>

<span data-ttu-id="3dd6a-122">Étendons cet exemple en créant un composant à l’aide d’une conception qui s’appuie sur des délégués.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-122">Let's build on that example by creating a component using a design that relies on delegates.</span></span>

<span data-ttu-id="3dd6a-123">Nous allons définir un composant qui peut être utilisé pour des messages de journaux dans un système de grande taille.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-123">Let's define a component that could be used for log messages in a large system.</span></span> <span data-ttu-id="3dd6a-124">Les composants de bibliothèque pourraient être utilisés dans de nombreux environnements différents, sur plusieurs plateformes différentes.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-124">The library components could be used in many different environments, on multiple different platforms.</span></span> <span data-ttu-id="3dd6a-125">Il existe de nombreuses fonctionnalités courantes dans le composant qui gère les journaux.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-125">There are a lot of common features in the component that manages the logs.</span></span> <span data-ttu-id="3dd6a-126">Il doit accepter des messages en provenance de tout composant du système.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-126">It will need to accept messages from any component in the system.</span></span> <span data-ttu-id="3dd6a-127">Ces messages auront des priorités différentes, que le composant principal peut gérer.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-127">Those messages will have different priorities, which the core component can manage.</span></span> <span data-ttu-id="3dd6a-128">Les messages doivent avoir des horodatages dans leur forme finale archivée.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-128">The messages should have timestamps in their final archived form.</span></span> <span data-ttu-id="3dd6a-129">Pour des scénarios avancés, vous pouvez filtrer les messages en fonction du composant source.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-129">For more advanced scenarios, you could filter messages by the source component.</span></span>

<span data-ttu-id="3dd6a-130">Il y a un aspect de la fonctionnalité qui changera souvent : l’emplacement d’écriture des messages.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-130">There is one aspect of the feature that will change often: where messages are written.</span></span> <span data-ttu-id="3dd6a-131">Dans certains environnements, ils pourront être écrits dans la console des erreurs.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-131">In some environments, they may be written to the error console.</span></span> <span data-ttu-id="3dd6a-132">Dans d’autres, il pourra s’agir d’un fichier.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-132">In others, a file.</span></span> <span data-ttu-id="3dd6a-133">Les autres possibilités incluent le stockage de base de données, les journaux des événements du système d’exploitation ou autre stockage de documents.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-133">Other possibilities include database storage, OS event logs, or other document storage.</span></span>

<span data-ttu-id="3dd6a-134">Il existe également des combinaisons de sortie qui peuvent être utilisées dans différents scénarios.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-134">There are also combinations of output that might be used in different scenarios.</span></span> <span data-ttu-id="3dd6a-135">Vous souhaiterez peut-être écrire des messages dans la console et dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-135">You may want to write messages to the console and to a file.</span></span>

<span data-ttu-id="3dd6a-136">Une conception basée sur des délégués offre une très grande souplesse et facilite la prise en charge des mécanismes de stockage qui pourront être ajoutés à l’avenir.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-136">A design based on delegates will provide a great deal of flexibility, and make it easy to support storage mechanisms that may be added in the future.</span></span>

<span data-ttu-id="3dd6a-137">Dans cette conception, le composant de journal principal peut être une classe non virtuelle, voire sealed.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-137">Under this design, the primary log component can be a non-virtual, even sealed class.</span></span> <span data-ttu-id="3dd6a-138">Vous pouvez incorporer n’importe quel jeu de délégués pour écrire les messages sur différents supports de stockage.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-138">You can plug in any set of delegates to write the messages to different storage media.</span></span> <span data-ttu-id="3dd6a-139">La prise en charge intégrée des délégués multicast facilite la prise en charge des scénarios où les messages doivent être écrits à plusieurs emplacements (dans un fichier et une console).</span><span class="sxs-lookup"><span data-stu-id="3dd6a-139">The built in support for multicast delegates makes it easy to support scenarios where messages must be written to multiple locations (a file, and a console).</span></span>

## <a name="a-first-implementation"></a><span data-ttu-id="3dd6a-140">Une première implémentation</span><span class="sxs-lookup"><span data-stu-id="3dd6a-140">A First Implementation</span></span>

<span data-ttu-id="3dd6a-141">Commençons par quelque chose de simple : l’implémentation initiale acceptera les nouveaux messages et les écrira à l’aide de n’importe quel délégué attaché.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-141">Let's start small: the initial implementation will accept new messages, and write them using any attached delegate.</span></span> <span data-ttu-id="3dd6a-142">Vous pouvez démarrer avec un délégué qui écrit des messages dans la console.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-142">You can start with one delegate that writes messages to the console.</span></span>

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(string msg)
    {
        WriteMessage(msg);
    }
}
```

<span data-ttu-id="3dd6a-143">La classe statique ci-dessus est la chose la plus simple qui peut fonctionner.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-143">The static class above is the simplest thing that can work.</span></span> <span data-ttu-id="3dd6a-144">Nous devons écrire l’implémentation unique pour la méthode qui écrit des messages dans la console :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-144">We need to write the single implementation for the method that writes messages to the console:</span></span> 

```csharp
public static void LogToConsole(string message)
{
    Console.Error.WriteLine(message);
}
```

<span data-ttu-id="3dd6a-145">Pour finir, nous devons raccorder le délégué en l’attachant au délégué WriteMessage déclaré dans l’enregistreur d’événements :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-145">Finally, you need to hook up the delegate by attaching it to the WriteMessage delegate declared in the logger:</span></span>

```csharp
Logger.WriteMessage += LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="3dd6a-146">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3dd6a-146">Practices</span></span>

<span data-ttu-id="3dd6a-147">Jusqu’à présent, notre exemple est assez simple, mais il illustre quand même certaines instructions importantes pour les conceptions impliquant des délégués.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-147">Our sample so far is fairly simple, but it still demonstrates some of the important guidelines for designs involving delegates.</span></span>

<span data-ttu-id="3dd6a-148">L’utilisation des types délégués définis dans le Core Framework permet aux utilisateurs de travailler facilement avec les délégués.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-148">Using the delegate types defined in the Core Framework makes it easier for users to work with the delegates.</span></span> <span data-ttu-id="3dd6a-149">Vous n’avez pas besoin de définir de nouveaux types, et les développeurs qui utilisent votre bibliothèque n’ont pas besoin d’apprendre de nouveaux types délégués spécialisés.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-149">You don't need to define new types, and developers using your library do not need to learn new, specialized delegate types.</span></span>

<span data-ttu-id="3dd6a-150">Les interfaces utilisées sont le plus minimal et flexible possible : pour créer un enregistreur d’événements de sortie, vous devez créer une méthode.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-150">The interfaces used are as minimal and as flexible as possible: To create a new output logger, you must create one method.</span></span> <span data-ttu-id="3dd6a-151">Il peut s’agir d’une méthode statique ou d’une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-151">That method may be a static method, or an instance method.</span></span> <span data-ttu-id="3dd6a-152">Elle peut avoir n’importe quel accès.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-152">It may have any access.</span></span>

## <a name="formatting-output"></a><span data-ttu-id="3dd6a-153">Mise en forme de sortie</span><span class="sxs-lookup"><span data-stu-id="3dd6a-153">Formatting Output</span></span>

<span data-ttu-id="3dd6a-154">Nous allons maintenant rendre cette première version un peu plus robuste et commencer à créer d’autres mécanismes de journalisation.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-154">Let's make this first version a bit more robust, and then start creating other logging mechanisms.</span></span>

<span data-ttu-id="3dd6a-155">Ensuite, nous ajouterons quelques arguments à la méthode `LogMessage()` pour que notre classe de journal crée des messages plus structurés :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-155">Next, let's add a few arguments to the `LogMessage()` method so that your log class creates more structured messages:</span></span>

```csharp
// Logger implementation two
public enum Severity
{
    Verbose,
    Trace,
    Information,
    Warning,
    Error,
    Critical
}

public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```

<span data-ttu-id="3dd6a-156">Maintenant, utilisons cet argument `Severity` pour filtrer les messages envoyés à la sortie du journal.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-156">Next, let's make use of that `Severity` argument to filter the messages that are sent to the log's output.</span></span> 

```csharp
public static class Logger
{
    public static Action<string> WriteMessage;
    
    public static Severity LogLevel {get;set;} = Severity.Warning;
    
    public static void LogMessage(Severity s, string component, string msg)
    {
        if (s < LogLevel)
            return;
            
        var outputMsg = $"{DateTime.Now}\t{s}\t{component}\t{msg}";
        WriteMessage(outputMsg);
    }
}
```
## <a name="practices"></a><span data-ttu-id="3dd6a-157">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3dd6a-157">Practices</span></span>

<span data-ttu-id="3dd6a-158">Nous avons ajouté de nouvelles fonctionnalités à l’infrastructure de journalisation.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-158">You've added new features to the logging infrastructure.</span></span> <span data-ttu-id="3dd6a-159">Le composant enregistreur d’événements étant très faiblement couplé à tout mécanisme de sortie, ces nouvelles fonctionnalités peuvent être ajoutées sans aucun impact sur le code qui implémente le délégué enregistreur d’événements.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-159">Because the logger component is very loosely coupled to any output mechanism, these new features can be added with no impact on any of the code implementing the logger delegate.</span></span>

<span data-ttu-id="3dd6a-160">Au fil du temps, vous verrez d’autres d’exemples montrant comment ce couplage faible autorise une plus grande souplesse dans la mise à jour des parties du site sans aucune modification des autres emplacements.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-160">As you keep building this, you'll see more examples of how this loose coupling enables greater flexibility in updating parts of the site without any changes to other locations.</span></span> <span data-ttu-id="3dd6a-161">En fait, dans une application plus grande, les classes de sortie de l’enregistreur d’événements peuvent être dans un autre assembly et ne même pas avoir besoin d’être reconstruites.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-161">In fact, in a larger application, the logger output classes might be in a different assembly, and not even need to be rebuilt.</span></span>

## <a name="building-a-second-output-engine"></a><span data-ttu-id="3dd6a-162">Création d’un deuxième moteur de sortie</span><span class="sxs-lookup"><span data-stu-id="3dd6a-162">Building a Second Output Engine</span></span>

<span data-ttu-id="3dd6a-163">Le composant journal commence à prendre forme.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-163">The Log component is coming along well.</span></span> <span data-ttu-id="3dd6a-164">Ajoutons un autre moteur de sortie qui enregistre les messages dans un fichier.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-164">Let's add one more output engine that logs messages to a file.</span></span> <span data-ttu-id="3dd6a-165">Ce moteur de sortie est légèrement plus complexe.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-165">This will be a slightly more involved output engine.</span></span> <span data-ttu-id="3dd6a-166">Il s’agit d’une classe qui encapsule les opérations de fichiers et garantit que le fichier est toujours fermé après chaque écriture.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-166">It will be a class that encapsulates the file operations, and ensures that the file is always closed after each write.</span></span> <span data-ttu-id="3dd6a-167">Cela permet de s’assurer que toutes les données sont vidées sur le disque après chaque génération de message.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-167">That ensures that all the data is flushed to disk after each message is generated.</span></span>

<span data-ttu-id="3dd6a-168">Voici cet enregistreur d’événements basé sur fichier :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-168">Here is that file based logger:</span></span>

```csharp
public class FileLogger
{
    private readonly string logPath;
    public FileLogger(string path)
    {
        logPath = path;
        Logger.WriteMessage += LogMessage;
    }
    
    public void DetachLog() => Logger.WriteMessage -= LogMessage;

    // make sure this can't throw.
    private void LogMessage(string msg)
    {
        try {
            using (var log = File.AppendText(logPath))
            {
                log.WriteLine(msg);
                log.Flush();
            }
        } catch (Exception e)
        {
            // Hmm. Not sure what to do.
            // Logging is failing...
        }
    }
}
```

<span data-ttu-id="3dd6a-169">Une fois que nous avons créé cette classe, nous pouvons l’instancier, et elle attache sa méthode LogMessage au composant enregistreur d’événements :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-169">Once you've created this class, you can instantiate it and it attaches its LogMessage method to the Logger component:</span></span>

```csharp
var file = new FileLogger("log.txt");
```

<span data-ttu-id="3dd6a-170">Ces deux méthodes ne s’excluent pas mutuellement.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-170">These two are not mutually exclusive.</span></span> <span data-ttu-id="3dd6a-171">Nous pourrions attacher les deux méthodes de journalisation et générer des messages dans la console et dans un fichier :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-171">You could attach both log methods and generate messages to the console and a file:</span></span>

```csharp
var fileOutput = new FileLogger("log.txt");
Logger.WriteMessage += LogToConsole;
```

<span data-ttu-id="3dd6a-172">Plus tard, même dans la même application, nous pourrions supprimer l’un des délégués sans provoquer d’autre problème dans le système :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-172">Later, even in the same application, you can remove one of the delegates without any other issues to the system:</span></span>

```csharp
Logger.WriteMessage -= LogToConsole;
```

## <a name="practices"></a><span data-ttu-id="3dd6a-173">Méthodes</span><span class="sxs-lookup"><span data-stu-id="3dd6a-173">Practices</span></span>

<span data-ttu-id="3dd6a-174">Nous avons maintenant ajouté un deuxième gestionnaire de sortie pour le sous-système de journalisation.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-174">Now, you've added a second output handler for the logging sub-system.</span></span>
<span data-ttu-id="3dd6a-175">Celui-ci a besoin d’un peu plus d’infrastructure pour correctement prendre en charge le système de fichiers.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-175">This one needs a bit more infrastructure to correctly support the file system.</span></span> <span data-ttu-id="3dd6a-176">Le délégué est une méthode d’instance.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-176">The delegate is an instance method.</span></span> <span data-ttu-id="3dd6a-177">Il s’agit aussi d’une méthode privée.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-177">It's also a private method.</span></span>
<span data-ttu-id="3dd6a-178">Une plus grande accessibilité n’est pas nécessaire, car l’infrastructure de délégué peut connecter les délégués.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-178">There's no need for greater accessibility because the delegate infrastructure can connect the delegates.</span></span>

<span data-ttu-id="3dd6a-179">Ensuite, la conception basée sur les délégués autorise plusieurs méthodes de sortie sans code supplémentaire.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-179">Second, the delegate-based design enables multiple output methods without any extra code.</span></span> <span data-ttu-id="3dd6a-180">Vous n’avez pas besoin de créer d’infrastructure supplémentaire pour prendre en charge plusieurs méthodes de sortie.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-180">You don't need to build any additional infrastructure to support multiple output methods.</span></span> <span data-ttu-id="3dd6a-181">Elles viennent simplement s’ajouter comme autre méthode dans la liste d’invocation.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-181">They simply become another method on the invocation list.</span></span>

<span data-ttu-id="3dd6a-182">Faites particulièrement attention au code de la méthode de sortie de journalisation de fichier.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-182">Pay special attention to the code in the file logging output method.</span></span> <span data-ttu-id="3dd6a-183">Cette méthode est codée pour s’assurer qu’elle ne lève pas d’exception.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-183">It is coded to ensure that it does not throw any exceptions.</span></span> <span data-ttu-id="3dd6a-184">Même si ce n’est pas toujours strictement nécessaire, cette pratique est souvent recommandée.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-184">While this isn't always strictly necessary, it's often a good practice.</span></span> <span data-ttu-id="3dd6a-185">Si l’une des méthodes délégué lève une exception, les délégués restants qui sont sur la liste d’invocation ne sont pas appelés.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-185">If either of the delegate methods throws an exception, the remaining delegates that are on the invocation won't be invoked.</span></span>

<span data-ttu-id="3dd6a-186">Dernière remarque : l’enregistreur d’événements de fichier doit gérer ses ressources en ouvrant et en fermant le fichier à chaque message de journal.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-186">As a last note, the file logger must manage its resources by opening and closing the file on each log message.</span></span> <span data-ttu-id="3dd6a-187">Vous pouvez choisir de laisser le fichier ouvert et d’implémenter IDisposable pour fermer le fichier une fois que vous avez terminé.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-187">You could choose to keep the file open and implement IDisposable to close the file when you are completed.</span></span>
<span data-ttu-id="3dd6a-188">Les deux méthodes ont leurs avantages et leurs inconvénients.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-188">Either method has its advantages and disadvantages.</span></span> <span data-ttu-id="3dd6a-189">Elles créent toutes les deux un peu plus de couplage entre les classes.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-189">Both do create a bit more coupling between the classes.</span></span>

<span data-ttu-id="3dd6a-190">Pour prendre en charge ces deux scénarios, il est inutile de mettre à jour le code de la classe Logger.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-190">None of the code in the Logger class would need to be updated in order to support either scenario.</span></span>

## <a name="handling-null-delegates"></a><span data-ttu-id="3dd6a-191">Gestion des délégués Null</span><span class="sxs-lookup"><span data-stu-id="3dd6a-191">Handling Null Delegates</span></span>

<span data-ttu-id="3dd6a-192">Pour finir, nous allons mettre à jour la méthode LogMessage afin qu’elle soit robuste pour les cas où aucun mécanisme de sortie n’est sélectionné.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-192">Finally, let's update the LogMessage method so that it is robust for those cases when no output mechanism is selected.</span></span> <span data-ttu-id="3dd6a-193">L’implémentation actuelle lève une `NullReferenceException` quand aucune liste d’invocation n’est attachée au délégué `WriteMessage`.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-193">The current implementation will throw a `NullReferenceException` when the `WriteMessage` delegate does not have an invocation list attached.</span></span>
<span data-ttu-id="3dd6a-194">Vous préférerez peut-être une conception qui continue en mode silencieux quand aucune méthode n’a été attachée.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-194">You may prefer a design that silently continues when no methods have been attached.</span></span> <span data-ttu-id="3dd6a-195">Pour cela, vous pouvez utiliser l’opérateur conditionnel null, combiné avec la méthode `Delegate.Invoke()` :</span><span class="sxs-lookup"><span data-stu-id="3dd6a-195">This is easy using the null conditional operator, combined with the `Delegate.Invoke()` method:</span></span>

```csharp
public static void LogMessage(string msg)
{
    WriteMessage?.Invoke(msg);
}
```

<span data-ttu-id="3dd6a-196">L’opérateur conditionnel null (`?.`) court-circuite quand l’opérande gauche (ici, `WriteMessage`) est null, ce qui signifie que le système ne tente pas de consigner un message dans le journal.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-196">The null conditional operator (`?.`) short-circuits when the left operand (`WriteMessage` in this case) is null, which means no attempt is made to log a message.</span></span>

<span data-ttu-id="3dd6a-197">Vous ne trouverez pas la méthode `Invoke()` répertoriée dans la documentation de `System.Delegate` ou `System.MulticastDelegate`.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-197">You won't find the `Invoke()` method listed in the documentation for `System.Delegate` or `System.MulticastDelegate`.</span></span> <span data-ttu-id="3dd6a-198">Le compilateur génère une méthode `Invoke` de type sécurisé pour tout type de délégué déclaré.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-198">The compiler generates a type safe `Invoke` method for any delegate type declared.</span></span> <span data-ttu-id="3dd6a-199">Dans cet exemple, cela signifie que `Invoke` prend un seul argument `string` et a un type de retour void.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-199">In this example, that means `Invoke` takes a single `string` argument, and has a void return type.</span></span>

## <a name="summary-of-practices"></a><span data-ttu-id="3dd6a-200">Récapitulatif des méthodes</span><span class="sxs-lookup"><span data-stu-id="3dd6a-200">Summary of Practices</span></span>

<span data-ttu-id="3dd6a-201">Nous venons de voir le début d’un composant de journal qui peut être étendu avec d’autres enregistreurs, ainsi que d’autres fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-201">You've seen the beginnings of a log component that could be expanded with other writers, and other features.</span></span> <span data-ttu-id="3dd6a-202">Grâce à l’utilisation de délégués dans la conception, ces différents composants sont très faiblement couplés.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-202">By using delegates in the design these different components are very loosely coupled.</span></span> <span data-ttu-id="3dd6a-203">Cela présente plusieurs avantages.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-203">This provides several advantages.</span></span> <span data-ttu-id="3dd6a-204">Il est très facile de créer de nouveaux mécanismes de sortie et de les attacher au système.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-204">It's very easy to create new output mechanisms and attach them to the system.</span></span> <span data-ttu-id="3dd6a-205">Ces autres mécanismes n’ont besoin que d’une seule méthode : celle qui écrit le message du journal.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-205">These other mechanisms only need one method: the method that writes the log message.</span></span> <span data-ttu-id="3dd6a-206">Cette conception offre une grande souplesse lors de l’ajout de nouvelles fonctionnalités.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-206">It's a design that is very resilient when new features are added.</span></span> <span data-ttu-id="3dd6a-207">Le contrat requis pour tout enregistreur consiste à implémenter une méthode.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-207">The contract required for any writer is to implement one method.</span></span> <span data-ttu-id="3dd6a-208">Il peut s’agir d’une méthode d’instance ou statique.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-208">That method could be a static or instance method.</span></span> <span data-ttu-id="3dd6a-209">Elle peut être publique, privée ou avoir tout autre accès légal.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-209">It could be public, private, or any other legal access.</span></span>

<span data-ttu-id="3dd6a-210">La classe Logger peut apporter des améliorations ou des modifications sans introduire de modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-210">The Logger class can make any number of enhancements or changes without introducing breaking changes.</span></span> <span data-ttu-id="3dd6a-211">Comme toute classe, vous ne pouvez pas modifier l’API publique sans risque de modifications avec rupture.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-211">Like any class, you cannot modify the public API without the risk of breaking changes.</span></span> <span data-ttu-id="3dd6a-212">Toutefois, le couplage entre l’enregistreur d’événements et les moteurs de sortie étant uniquement par l’intermédiaire du délégué, aucun autre type (tel que les interfaces ou classes de base) n’est appelé.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-212">But, because the coupling between the logger and any output engines is only through the delegate, no other types (like interfaces or base classes) are involved.</span></span> <span data-ttu-id="3dd6a-213">Le couplage est aussi réduit que possible.</span><span class="sxs-lookup"><span data-stu-id="3dd6a-213">The coupling is as small as possible.</span></span>

[<span data-ttu-id="3dd6a-214">Suivant</span><span class="sxs-lookup"><span data-stu-id="3dd6a-214">Next</span></span>](events-overview.md)


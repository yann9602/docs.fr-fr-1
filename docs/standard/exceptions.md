---
title: "Gestion et levée d’exceptions dans .NET"
description: Guide pratique pour utiliser des exceptions dans .NET
keywords: .NET, .NET Core
author: mairaw
manager: wpickett
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.technology: .net-core-technologies
ms.devlang: dotnet
ms.assetid: bf116df6-0042-46bf-be13-b69864816210
translationtype: Human Translation
ms.sourcegitcommit: 9584699ad7e745ae3cb059b1bb8327301c9a3286
ms.openlocfilehash: 0c73fb0a12092877ff5b54221f4a80693d1d1152

---

# <a name="handling-and-throwing-exceptions-in-net"></a>Gestion et levée d’exceptions dans .NET

Les applications doivent pouvoir gérer de manière cohérente les erreurs qui se produisent au moment de l'exécution. .NET fournit un modèle pour avertir les applications de façon uniforme de la présence d’erreurs : les opérations .NET indiquent un échec en levant des exceptions.

## <a name="exceptions"></a>Exceptions

Une exception est une condition d'erreur ou un comportement inattendu rencontré par un programme en cours d'exécution. Les exceptions peuvent être levées à cause d’une erreur dans votre code ou dans le code que vous appelez (une bibliothèque partagée, par exemple), de ressources de système d’exploitation non disponibles, de conditions inattendues rencontrées par le runtime (du code qui ne peut pas être vérifié, par exemple), etc. Votre application peut récupérer suite à certaines de ces conditions, mais pas toutes. Bien que vous puissiez récupérer suite à la plupart des exceptions d'application, vous ne pouvez pas récupérer suite à la plupart des exceptions runtime.

Dans .NET, une exception est un objet qui hérite de la classe [System.Exception](xref:System.Exception). Une exception est levée à partir d'une partie du code où un problème s'est produit. L'exception remonte la pile jusqu'à sa prise en charge par l'application ou l'arrêt du programme.

## <a name="exceptions-vs-traditional-errorhandling-methods"></a>Comparaison des exceptions et des méthodes traditionnelles de gestion des erreurs

Traditionnellement, le modèle de gestion des erreurs d'un langage reposait soit sur le mode unique utilisé par le langage en question pour détecter des erreurs et leur trouver des gestionnaires appropriés, soit sur le mécanisme de gestion des erreurs fourni par le système d'exploitation. La façon dont .NET implémente la gestion des exceptions offre les avantages suivants :

- La gestion et la levée des exceptions fonctionne de la même façon pour les langages de programmation .NET.

- Ne requiert aucune syntaxe particulière pour la gestion des exceptions, mais laisse chaque langage définir sa propre syntaxe.

- Les exceptions peuvent être levées au-delà des limites des processus et même des ordinateurs.

- Un code de gestion des exceptions peut être ajouté à une application pour augmenter la fiabilité du programme.

Les exceptions offrent des avantages par rapport à d’autres méthodes de notification des erreurs, comme les codes de retour. Les erreurs ne passent pas inaperçues, car si une exception est levée et que vous ne la gérez pas, le runtime arrête votre application. Les valeurs non valides ne continuent pas à se propager dans le système parce que du code n’a pas pu vérifier un code de retour d’échec. 

## <a name="exception-class-and-properties"></a>Classe et propriétés d’exception

La classe @System.Exception est la classe de base dont héritent les exceptions. Par exemple, la hiérarchie de classes @System.InvalidCastException se présente comme suit :

```
Object
  Exception
    SystemException
       InvalidCastException
```

La classe @System.Exception a les propriétés suivantes qui vous permettront de mieux comprendre une exception.

| Nom de propriété | Description |
| ------------- | ----------- |
| @System.Exception.Data | @System.Collections.IDictionary qui contient des données arbitraires dans des paires clé-valeur. |
| @System.Exception.HelpLink | Peut contenir une URL (ou URN) vers un fichier d’aide qui fournit des informations détaillées sur la cause d’une exception. |
| @System.Exception.InnerException | Cette propriété peut être utilisée pour créer et conserver une série d’exceptions pendant la gestion des exceptions. Vous pouvez l’utiliser pour créer une exception qui contient des exceptions interceptées précédemment. L’exception d’origine peut être capturée par la deuxième exception dans la propriété @System.Exception.InnerException, ce qui permet au code qui gère la deuxième exception d’examiner les informations supplémentaires. Par exemple, supposons que vous disposez d’une méthode qui reçoit un argument avec une mise en forme incorrecte.  Le code essaie de lire l’argument, mais une exception est levée. La méthode intercepte l’exception et lève une exception @System.FormatException. Pour améliorer la capacité de l’appelant à déterminer la raison pour laquelle une exception est levée, il est parfois souhaitable qu’une méthode intercepte une exception levée par une routine d’assistance, puis qu’elle lève une exception plus évocatrice de l’erreur qui s’est produite. Une exception plus significative peut être créée, dans laquelle la référence à l’exception interne peut être définie sur l’exception d’origine. Cette exception plus significative peut ensuite être levée pour l’appelant. Notez que cette fonctionnalité vous permet de créer une série d’exceptions liées qui se termine avec l’exception initialement levée. |
| @System.Exception.Message | Fournit les détails de la cause d’une exception.
| @System.Exception.Source | Obtient ou définit le nom de l'application ou de l'objet qui est à l'origine de l'erreur. |
| @System.Exception.StackTrace | Contient une trace de pile qui peut être utilisée pour déterminer où une erreur s’est produite. La trace de la pile comprend le nom du fichier source et le numéro de ligne du programme si les informations de débogage sont disponibles. |

La plupart des classes qui héritent de @System.Exception n’implémentent pas de membres supplémentaires et ne fournissent pas de fonctionnalités supplémentaires. Elles héritent simplement de @System.Exception. Par conséquent, vous pouvez trouver les informations les plus importantes d’une exception dans la hiérarchie des classes d’exception, le nom de l’exception et les informations contenues dans l’exception.

Nous vous recommandons de lever et d’intercepter uniquement des objets qui dérivent de @System.Exception,, mais vous pouvez lever comme exception n’importe quel objet qui dérive de la classe @System.Object. Notez que tous les langages ne prennent pas forcément en charge la levée et l’interception d’objets qui ne dérivent pas de @System.Exception.

## <a name="common-exceptions"></a>Exceptions courantes

Le tableau suivant répertorie certaines exceptions courantes avec des exemples de cause possible.

| Type d'exception | Type de base | Description | Exemple |
| -------------- | --------- | ----------- | ------- |
| @System.Exception | @System.Object | Classe de base pour toutes les exceptions. | Aucun (utilisez une classe dérivée de cette exception). |
| @System.IndexOutOfRangeException | @System.Exception | Levée par le runtime uniquement en cas d’indexation incorrecte du tableau. | Indexation d’un tableau en dehors de sa plage valide : `arr[arr.Length+1]` |
| @System.NullReferenceException | @System.Exception | Levée par le runtime uniquement si un objet Null est référencé. | `object o = null; o.ToString();` |
| @System.InvalidOperationException | @System.Exception | Levée par les méthodes en cas d’état non valide. | Appel de `Enumerator.GetNext()` après la suppression d’un élément de la collection sous-jacente. |
| @System.ArgumentException | @System.Exception | Classe de base pour toutes les exceptions d’argument. | Aucun (utilisez une classe dérivée de cette exception). |
| @System.ArgumentNullException | @System.Exception | Levée par les méthodes qui n’acceptent pas la valeur Null pour un argument. | `String s = null; "Calculate".IndexOf (s);` |
| @System.ArgumentOutOfRangeException | @System.Exception | Levée par les méthodes qui vérifient que les arguments sont inclus dans une plage donnée. | `String s = "string"; s.Substring(s.Length+1);` |

## <a name="how-to-use-the-trycatch-block-to-catch-exceptions"></a>Guide pratique pour utiliser le bloc try/catch pour intercepter des exceptions

Placez les sections de code qui peuvent lever des exceptions dans un bloc `try` et placez le code qui gère les exceptions dans un bloc `catch`. Le bloc `catch` est une série d’instructions qui commencent par le mot clé `catch`, suivi d’un type d’exception et d’une action à effectuer.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception possible. La méthode `Main` contient un bloc `try` avec une instruction @System.IO.StreamReader qui ouvre un fichier de données appelé `data.txt` et écrit une chaîne à partir du fichier. À la suite du bloc `try`, un bloc `catch` intercepte toute exception qui résulte du bloc `try`.

C#
```
using System;
using System.IO;

public class ProcessFile
{
    public static void Main()
    {
        try
        {
            StreamReader sr = File.OpenText("data.txt");
            Console.WriteLine("The first line of this file is {0}", sr.ReadLine());
            sr.Dispose();
        }
        catch (Exception e)
        {
            Console.WriteLine("An error occurred: '{0}'", e);
        }
    }
}
```

Le Common Language Runtime intercepte les exceptions qui ne sont pas interceptées par un bloc catch. Selon la configuration du runtime, une boîte de dialogue de débogage s’affiche, le programme s’arrête et une boîte de dialogue s’affiche avec des informations sur l’exception, ou une erreur est imprimée dans STDERR.

> [!NOTE] 
> Toute ligne de code ou presque peut générer une exception, notamment les exceptions qui sont levées par le Common Language Runtime lui-même, telles que @System.OutOfMemoryException. La plupart des applications n’ont pas à traiter ces exceptions, mais vous devez être conscient de cette possibilité quand vous écrivez des bibliothèques destinées à d’autres utilisateurs. Afin d’obtenir des suggestions pour savoir quand définir du code dans un bloc Try, consultez les [Bonnes pratiques pour les exceptions](#best-practices-for-exceptions).
 
## <a name="how-to-use-specific-exceptions-in-a-catch-block"></a>Guide pratique pour utiliser des exceptions spécifiques dans un bloc Catch

L’exemple de code précédent illustre une instruction `catch` de base qui intercepte toutes les exceptions. En général, cependant, il est conseillé en programmation d’intercepter un type d’exception spécifique au lieu d’utiliser une instruction `catch` de base.

Quand une exception se produit, elle remonte la pile et chaque bloc catch a la possibilité de la gérer. L’ordre des instructions catch est important. Placez les blocs catch ciblés sur des exceptions spécifiques avant un bloc catch d’exceptions générales, sinon le compilateur peut générer une erreur. Le bloc catch approprié est déterminé en mettant en correspondance le type de l’exception avec le nom de l’exception spécifiée dans le bloc catch. S’il n’existe aucun bloc catch spécifique, l’exception est interceptée par un bloc catch général, le cas échéant.

Le code suivant exemple utilise un bloc `try`/`catch` pour intercepter @System.InvalidCastException. L’exemple crée une classe appelée `Employee` avec une propriété unique, `Emlevel` (niveau de l’employé). Une méthode `PromoteEmployee` prend un objet et incrémente le niveau de l’employé. Une exception @System.InvalidCastException se produit quand une instance @System.DateTime est passée à la méthode `PromoteEmployee`.

C#
```
using System;

public class Employee
{
    //Create employee level property.
    public int Emlevel
    {
        get
        {
            return(emlevel);
        }
        set
        {
            emlevel = value;
        }
    }

    private int emlevel = 0;
}

public class Ex13
{
    public static void PromoteEmployee(Object emp)
    {
        //Cast object to Employee.
        Employee e = (Employee) emp;
        // Increment employee level.
        e.Emlevel = e.Emlevel + 1;
    }

    public static void Main()
    {
        try
        {
            Object o = new Employee();
            DateTime newyears = new DateTime(2001, 1, 1);
            //Promote the new employee.
            PromoteEmployee(o);
            //Promote DateTime; results in InvalidCastException as newyears is not an employee instance.
            PromoteEmployee(newyears);
        }
        catch (InvalidCastException e)
        {
            Console.WriteLine("Error passing data to PromoteEmployee method. " + e.Message);
        }
    }
}
```

## <a name="how-to-use-finally-blocks"></a>Guide pratique pour utiliser des blocs finally

Quand une exception se produit, l’exécution s’arrête et le contrôle est donné au gestionnaire d’exceptions approprié. Cela signifie souvent que les lignes de code qui doivent être exécutées sont ignorées. Un nettoyage des ressources, comme la fermeture d’un fichier, doit être effectué même si une exception est levée. Pour ce faire, vous pouvez utiliser un bloc `finally`. Un bloc `finally` s’exécute toujours, qu’une exception soit levée ou non.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une exception @System.ArgumentOutOfRangeException. La méthode `Main` crée deux tableaux et tente de copier l’un dans l’autre. Cette action génère une exception @System.ArgumentOutOfRangeException et l’erreur est écrite dans la console. Le bloc `finally` s’exécute indépendamment du résultat de l’action de copie.

C#
```
using System;

class ArgumentOutOfRangeExample
{
    public static void Main()
    {
        int[] array1 = {0, 0};
        int[] array2 = {0, 0};

        try
        {
            Array.Copy(array1, array2, -1);
        }
        catch (ArgumentOutOfRangeException e)
        {
            Console.WriteLine("Error: {0}", e);
        }
        finally
        {
            Console.WriteLine("This statement is always executed.");
        }
    }
}
```

## <a name="how-to-explicitly-throw-exceptions"></a>Guide pratique pour lever explicitement des exceptions

Vous pouvez lever explicitement une exception à l’aide de l’instruction `throw`. Vous pouvez aussi lever de nouveau une exception interceptée à l’aide de l’instruction `throw`. En codage, il est conseillé d’ajouter des informations à une exception levée une deuxième fois pour fournir plus d’informations durant le débogage.

L’exemple de code suivant utilise un bloc `try`/`catch` pour intercepter une éventuelle exception @System.IO.FileNotFoundException. À la suite du bloc `try`, un bloc `catch` intercepte l’exception @System.IO.FileNotFoundException et écrit un message dans la console si le fichier de données est introuvable. L’instruction suivante est `throw`, qui lève une nouvelle exception @System.IO.FileNotFoundException et ajoute des informations de texte à l’exception.

C#
```
using System;
using System.IO;

public class ProcessFile
{
   public static void Main()
      {
      FileStream fs = null;
      try   
      {
         //Opens a text tile.
         fs = new FileStream(@"C:\temp\data.txt", FileMode.Open);
         StreamReader sr = new StreamReader(fs);
         string line;

         //A value is read from the file and output to the console.
         line = sr.ReadLine();
         Console.WriteLine(line);
      }
      catch(FileNotFoundException e)
      {
         Console.WriteLine("[Data File Missing] {0}", e);
         throw new FileNotFoundException(@"[data.txt not in c:\temp directory]",e);
      }
      finally
      {
         if (fs != null)
            fs.Dispose();
      }
   }
}
```

## <a name="how-to-create-userdefined-exceptions"></a>Guide pratique pour créer des exceptions définies par l’utilisateur

.NET fournit une hiérarchie de classes d’exceptions qui sont en fin de compte dérivées de la classe de base @System.Exception. Toutefois, si aucune exception prédéfinie ne répond à vos besoins, vous pouvez créer vos propres classes d’exception en les dérivant de la classe @System.Exception.

Quand vous créez vos propres exceptions, terminez le nom de la classe définie par l’utilisateur par le mot « Exception » et implémentez les trois constructeurs communs, comme indiqué dans l’exemple suivant. L’exemple définit une nouvelle classe d’exception nommée `EmployeeListNotFoundException`. La classe est dérivée de l’exception @System.Exception et inclut trois constructeurs.

C#
```
using System;

public class EmployeeListNotFoundException: Exception
{
    public EmployeeListNotFoundException()
    {
    }

    public EmployeeListNotFoundException(string message)
        : base(message)
    {
    }

    public EmployeeListNotFoundException(string message, Exception inner)
        : base(message, inner)
    {
    }
}
```

> [!NOTE]
> Dans les situations où vous utilisez la communication à distance, vous devez vérifier que les métadonnées des exceptions définies par l’utilisateur sont disponibles sur le serveur (appelé) et le client (objet proxy ou appelant). Pour plus d’informations, consultez les [Bonnes pratiques pour les exceptions](#best-practices-for-exceptions).

## <a name="best-practices-for-exceptions"></a>Bonnes pratiques pour les exceptions

Une application bien conçue gère les exceptions et les erreurs pour empêcher les incidents d'applications. Cette section présente les bonnes pratiques pour la gestion et la création des exceptions.

### <a name="use-trycatchfinally-blocks"></a>Utiliser des blocs try/catch/finally

Utilisez des blocs `try`/`catch`/`finally` autour du code susceptible de générer une exception. 

Dans les blocs `catch`, veillez à toujours classer les exceptions de la plus spécifique à la moins spécifique.

Utilisez un bloc `finally` pour nettoyer les ressources, que la récupération soit possible ou non.

### <a name="handle-common-conditions-without-throwing-exceptions"></a>Gérer les conditions courantes sans lever d’exception

En ce qui concerne les conditions susceptibles de se produire, mais pouvant déclencher une exception, gérez-les de façon à éviter l’exception. Par exemple, si vous essayez de fermer une connexion déjà fermée, vous obtenez une exception `InvalidOperationException`. Vous pouvez l’éviter avec une instruction `if` qui permet de vérifier l’état de la connexion avant d’essayer de la fermer.

C#
```
if (conn.State != ConnectionState.Closed)
{
    conn.Close();
}
```

Si vous ne vérifiez pas l’état de la connexion avant de la fermer, vous pouvez intercepter l’exception `InvalidOperationException`.

C#
```
try
{
    conn.Close();
}
catch (InvalidOperationException ex)
{
    Console.WriteLine(ex.GetType().FullName);
    Console.WriteLine(ex.Message);
}
```

Le choix de la méthode dépend de la fréquence à laquelle l’événement doit se produire.

- Utilisez la gestion des exceptions si l'événement ne se produit pas très souvent, c'est-à-dire, si l'événement est véritablement exceptionnel et indique une erreur (telle qu'une fin de fichier inattendue). Lorsque vous utilisez la gestion des exceptions, la quantité de code exécutée en situation normale est moindre.

- Recherchez les conditions d’erreur dans le code si l’événement se produit régulièrement et peut être considéré comme faisant partie de l’exécution normale. Quand vous recherchez les conditions d’erreur courantes, vous exécutez moins de code, car vous évitez les exceptions.

### <a name="design-classes-so-that-exceptions-can-be-avoided"></a>Concevoir des classes pour éviter les exceptions

Une classe peut fournir des méthodes ou propriétés qui vous permettent d’éviter d’effectuer un appel susceptible de déclencher une exception. Par exemple, une classe @System.IO.FileStream fournit des méthodes qui permettent de déterminer si la fin du fichier a été atteinte. Ces méthodes peuvent servir à éviter l’exception qui est levée si vous dépassez la fin du fichier pendant la lecture. L’exemple suivant montre comment lire un fichier jusqu’à la fin sans lever d’exception.

C#
```
class FileRead
{
    public void ReadAll(FileStream fileToRead)
    {
        // This if statement is optional
        // as it is very unlikely that
        // the stream would ever be null.
        if (fileToRead == null)
        {
            throw new System.ArgumentNullException();
        }

        int b;

        // Set the stream position to the beginning of the file.
        fileToRead.Seek(0, SeekOrigin.Begin);

        // Read each byte to the end of the file.
        for (int i = 0; i < fileToRead.Length; i++)
        {
            b = fileToRead.ReadByte();
            Console.Write(b.ToString());
            // Or do something else with the byte.
        }
    }
}
```

Un autre moyen d’éviter les exceptions est de retourner Null pour les cas d’erreur très répandus au lieu de lever une exception. Un cas d'erreur très répandu peut être considéré comme un flux de contrôle normal. En retournant null dans ces cas-là, vous réduisez l'impact sur les performances d'une application.

### <a name="throw-exceptions-instead-of-returning-an-error-code"></a>Lever des exceptions au lieu de retourner un code d’erreur

Les exceptions font en sorte que les échecs ne passent pas inaperçus parce que l’appel du code n’a pas vérifié le code de retour. 

### <a name="use-the-predefined-net-exception-types"></a>Utiliser les types d’exception .NET prédéfinis

N'introduisez une nouvelle classe d'exception que quand aucune classe d'exception prédéfinie ne s'applique. Par exemple :

- Levez une exception @System.InvalidOperationException si un appel de jeu de propriétés ou de méthode n'est pas approprié étant donné l'état actuel de l'objet.

- Levez une exception @System.ArgumentException ou l’une des classes prédéfinies qui dérivent de @System.ArgumentException si des paramètres non valides sont passés.

### <a name="end-exception-class-names-with-the-word-exception"></a>Terminer les noms de classes d’exception par le mot `Exception`

Quand une exception personnalisée est nécessaire, nommez-la de manière appropriée et dérivez-la de la classe @System.Exception. Par exemple :

C#
```
public class MyFileNotFoundException : Exception
{
}
```

### <a name="include-three-constructors-in-custom-exception-classes"></a>Inclure trois constructeurs dans des classes d’exception personnalisées

Utilisez au moins les trois constructeurs communs pendant la création de vos propres classes d’exception : le constructeur par défaut, un constructeur qui prend un message de type chaîne et un constructeur qui prend un message de type chaîne et une exception interne.

- @System.Exception.%23ctor,, qui utilise les valeurs par défaut.

- @System.Exception.%23ctor(System.String),, qui accepte un message de type chaîne.

- @System.Exception.%23ctor(System.String,System.Exception),, qui accepte un message de type chaîne et une exception interne.

Pour obtenir un exemple, consultez [Guide pratique : créer des exceptions définies par l’utilisateur](#how-to-create-user-defined-exceptions).

### <a name="ensure-that-exception-data-is-available-when-code-executes-remotely"></a>Vérifier que les données d’exception sont disponibles quand le code s’exécute à distance

Quand vous créez des exceptions définies par l’utilisateur, vous devez vérifier que les métadonnées des exceptions sont disponibles pour le code qui s’exécute à distance. 

Par exemple, sur les runtimes .NET qui implémentent des domaines d’application, des exceptions peuvent se produire entre domaines d’application. Supposons que le domaine d’application A crée le domaine d’application B, lequel exécute du code qui lève une exception. Pour que le domaine d’application A intercepte et gère l’exception correctement, il doit pouvoir trouver l’assembly qui contient l’exception levée par le domaine d’application B. Si le domaine d’application B lève une exception qui est contenue dans un assembly sous sa base d’application, mais pas sous la base d’application du domaine d’application A, le domaine d’application A ne peut pas trouver l’exception et le Common Language Runtime lève une exception @System.IO.FileNotFoundException. Pour éviter cette situation, vous pouvez déployer l'assembly qui contient les informations sur les exceptions de deux façons :

- Placez l'assembly dans une base d'application commune partagée par les deux domaines d'application.

    \- ou -

- Si les domaines ne partagent pas une base d'application commune, signez l'assembly qui contient les informations sur les exceptions à l'aide d'un nom fort et déployez l'assembly dans le Global Assembly Cache.

### <a name="include-a-localized-description-string-in-every-exception"></a>Inclure une chaîne de description localisée dans chaque exception

Le message d’erreur que l’utilisateur voit est dérivé de la chaîne de description de l’exception qui a été levée et non du nom de la classe d’exception.

### <a name="use-grammatically-correct-error-messages"></a>Utiliser des messages d’erreur grammaticalement corrects

Écrivez des phrases claires et insérez une ponctuation finale. Chaque phrase de la chaîne de description d'une exception doit se terminer par un point. Par exemple, « La table du journal a débordé. » est une chaîne de description appropriée.

### <a name="in-custom-exceptions-provide-additional-properties-as-needed"></a>Dans les exceptions personnalisées, fournir des propriétés supplémentaires si nécessaire

Fournissez des propriétés supplémentaires (autres que la chaîne de description) pour une exception uniquement s'il existe un scénario par programmation dans lequel les informations supplémentaires sont utiles. Par exemple, la classe @System.IO.FileNotFoundException fournit la propriété @System.IO.FileNotFoundException.FileName.

### <a name="place-throw-statements-so-that-the-stack-trace-will-be-helpful"></a>Placer des instructions throw pour que la trace de la pile soit utile

La trace de la pile commence à l'instruction où l'exception est levée et se termine à l'instruction `catch` qui intercepte l'exception.

### <a name="use-exception-builder-methods"></a>Utiliser des méthodes de générateur d’exceptions

Il est fréquent qu'une classe lève la même exception à partir de différents endroits de son implémentation. Pour éviter un excès de code, utilisez des méthodes d'assistance qui créent une exception et la retournent. Exemple :

C#
```
class FileReader
{
    private string fileName;

    public FileReader(string path)
    {
        fileName = path;
    }

    public byte[] Read(int bytes)
    {
        byte[] results = FileUtils.ReadFromFile(fileName, bytes);
        if (results == null)
        {
            throw NewFileIOException();
        }
        return results;
    }

    FileReaderException NewFileIOException()
    {
        string description = "My NewFileIOException Description";

        return new FileReaderException(description);
    }
}

```

Dans certains cas, il est plus approprié d’utiliser le constructeur de l’exception pour générer l’exception. Par exemple, une classe d’exception globale comme @System.ArgumentException, 

### <a name="clean-up-intermediate-results-when-throwing-an-exception"></a>Nettoyer les résultats intermédiaires quand vous levez une exception

Les appelants doivent supposer qu'il n'y a aucun effet secondaire quand une exception est levée à partir d'une méthode. Par exemple, si vous avez du code qui transfère de l’argent en le retirant d’un compte pour le déposer dans un autre, et qu’une exception est levée pendant l’exécution du transfert, vous ne voulez pas que le retrait reste en vigueur.

C#
```
public void TransferFunds(Account from, Account to, decimal amount)
{
    from.Withdrawal(amount);
    // If the deposit fails, the withdrawal shouldn't remain in effect. 
    to.Deposit(amount);
}
```

Pour gérer cette situation, vous pouvez intercepter toutes les exceptions levées par la transaction de dépôt et annuler le retrait.

C#
```
private static void TransferFunds(Account from, Account to, decimal amount)
{
    string withdrawalTrxID = from.Withdrawal(amount);
    try
    {
        to.Deposit(amount);
    }
    catch
    {
        from.RollbackTransaction(withdrawalTrxID);
        throw
    }
}
```

Cet exemple illustre l’utilisation de `throw` pour lever de nouveau l’exception d’origine, ce qui peut permettre aux appelants de voir plus facilement la véritable cause du problème sans avoir à examiner la propriété @System.Exception.InnerException. Vous pouvez aussi lever une nouvelle exception et inclure l’exception d’origine comme exception interne :

C#
```
catch (Exception ex)
{
    from.RollbackTransaction(withdrawalTrxID);
    throw new Exception("Withdrawal failed", ex);
}
```

## <a name="see-also"></a>Voir aussi

Pour en savoir plus sur le fonctionnement des exceptions dans .NET, consultez [What Every Dev needs to Know About Exceptions in the Runtime](https://github.com/dotnet/coreclr/blob/master/Documentation/botr/exceptions.md) (Tout ce que doit savoir un développeur sur les exceptions dans le runtime).



<!--HONumber=Nov16_HO1-->



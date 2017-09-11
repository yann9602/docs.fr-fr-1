---
title: "Création et levée d'exceptions (Guide de programmation C#)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- catching exceptions [C#]
- throwing exceptions [C#]
- exceptions [C#], creating
- exceptions [C#], throwing
ms.assetid: 6bbba495-a115-4c6d-90cc-1f4d7b5f39e2
caps.latest.revision: 28
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f49b0911aa94480988987f209bc73d187451620
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="creating-and-throwing-exceptions-c-programming-guide"></a><span data-ttu-id="6d600-102">Création et levée d'exceptions (Guide de programmation C#)</span><span class="sxs-lookup"><span data-stu-id="6d600-102">Creating and Throwing Exceptions (C# Programming Guide)</span></span>
<span data-ttu-id="6d600-103">Les exceptions sont utilisées pour indiquer qu’une erreur s’est produite pendant l’exécution du programme.</span><span class="sxs-lookup"><span data-stu-id="6d600-103">Exceptions are used to indicate that an error has occurred while running the program.</span></span> <span data-ttu-id="6d600-104">Les objets d’exception qui décrivent une erreur sont créés, puis *levés* avec le mot clé [throw](../../../csharp/language-reference/keywords/throw.md).</span><span class="sxs-lookup"><span data-stu-id="6d600-104">Exception objects that describe an error are created and then *thrown* with the [throw](../../../csharp/language-reference/keywords/throw.md) keyword.</span></span> <span data-ttu-id="6d600-105">Le runtime recherche ensuite le gestionnaire d’exceptions le plus compatible.</span><span class="sxs-lookup"><span data-stu-id="6d600-105">The runtime then searches for the most compatible exception handler.</span></span>  
  
 <span data-ttu-id="6d600-106">Les programmeurs doivent lever des exceptions quand une ou plusieurs des conditions suivantes sont vérifiées :</span><span class="sxs-lookup"><span data-stu-id="6d600-106">Programmers should throw exceptions when one or more of the following conditions are true:</span></span>  
  
-   <span data-ttu-id="6d600-107">La méthode ne peut pas remplir sa fonction définie.</span><span class="sxs-lookup"><span data-stu-id="6d600-107">The method cannot complete its defined functionality.</span></span>  
  
     <span data-ttu-id="6d600-108">Par exemple, si un paramètre d’une méthode a une valeur non valide :</span><span class="sxs-lookup"><span data-stu-id="6d600-108">For example, if a parameter to a method has an invalid value:</span></span>  
  
     <span data-ttu-id="6d600-109">[!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d600-109">[!code-cs[csProgGuideExceptions#12](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_1.cs)]</span></span>  
  
-   <span data-ttu-id="6d600-110">Un appel inapproprié à un objet est effectué en fonction de l’état de l’objet.</span><span class="sxs-lookup"><span data-stu-id="6d600-110">An inappropriate call to an object is made, based on the object state.</span></span>  
  
     <span data-ttu-id="6d600-111">Une tentative d’écriture dans un fichier en lecture seule en est un exemple.</span><span class="sxs-lookup"><span data-stu-id="6d600-111">One example might be trying to write to a read-only file.</span></span> <span data-ttu-id="6d600-112">Dans les cas où l’état d’un objet n’autorise pas une opération, levez une instance d’<xref:System.InvalidOperationException> ou un objet basé sur une dérivation de cette classe.</span><span class="sxs-lookup"><span data-stu-id="6d600-112">In cases where an object state does not allow an operation, throw an instance of <xref:System.InvalidOperationException> or an object based on a derivation of this class.</span></span> <span data-ttu-id="6d600-113">Voici un exemple d’une méthode qui lève un objet <xref:System.InvalidOperationException> :</span><span class="sxs-lookup"><span data-stu-id="6d600-113">This is an example of a method that throws an <xref:System.InvalidOperationException> object:</span></span>  
  
     <span data-ttu-id="6d600-114">[!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d600-114">[!code-cs[csProgGuideExceptions#13](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_2.cs)]</span></span>  
  
-   <span data-ttu-id="6d600-115">Quand un argument d’une méthode provoque une exception.</span><span class="sxs-lookup"><span data-stu-id="6d600-115">When an argument to a method causes an exception.</span></span>  
  
     <span data-ttu-id="6d600-116">Dans ce cas, l’exception d’origine doit être interceptée et une instance d’<xref:System.ArgumentException> doit être créée.</span><span class="sxs-lookup"><span data-stu-id="6d600-116">In this case, the original exception should be caught and an <xref:System.ArgumentException> instance should be created.</span></span> <span data-ttu-id="6d600-117">L’exception d’origine doit être passée au constructeur d’<xref:System.ArgumentException> comme paramètre <xref:System.Exception.InnerException%2A> :</span><span class="sxs-lookup"><span data-stu-id="6d600-117">The original exception should be passed to the constructor of the <xref:System.ArgumentException> as the <xref:System.Exception.InnerException%2A> parameter:</span></span>  
  
     <span data-ttu-id="6d600-118">[!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d600-118">[!code-cs[csProgGuideExceptions#14](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_3.cs)]</span></span>  
  
 <span data-ttu-id="6d600-119">Les exceptions contiennent une propriété nommée <xref:System.Exception.StackTrace%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d600-119">Exceptions contain a property named <xref:System.Exception.StackTrace%2A>.</span></span> <span data-ttu-id="6d600-120">Cette chaîne contient le nom des méthodes sur la pile des appels actuelle, avec le nom de fichier et le numéro de ligne où l’exception a été levée pour chaque méthode.</span><span class="sxs-lookup"><span data-stu-id="6d600-120">This string contains the name of the methods on the current call stack, together with the file name and line number where the exception was thrown for each method.</span></span> <span data-ttu-id="6d600-121">Un objet <xref:System.Exception.StackTrace%2A> est créé automatiquement par le CLR (Common Language Runtime) à partir du point de l’instruction `throw`, de sorte que les exceptions doivent être levées à partir du point où la trace de la pile doit commencer.</span><span class="sxs-lookup"><span data-stu-id="6d600-121">A <xref:System.Exception.StackTrace%2A> object is created automatically by the common language runtime (CLR) from the point of the `throw` statement, so that exceptions must be thrown from the point where the stack trace should begin.</span></span>  
  
 <span data-ttu-id="6d600-122">Toutes les exceptions contiennent une propriété nommée <xref:System.Exception.Message%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d600-122">All exceptions contain a property named <xref:System.Exception.Message%2A>.</span></span> <span data-ttu-id="6d600-123">Cette chaîne doit être définie pour expliquer la raison de l’exception.</span><span class="sxs-lookup"><span data-stu-id="6d600-123">This string should be set to explain the reason for the exception.</span></span> <span data-ttu-id="6d600-124">Notez que les informations sensibles du point de vue de la sécurité ne doivent pas être placées dans le texte du message.</span><span class="sxs-lookup"><span data-stu-id="6d600-124">Note that information that is sensitive to security should not be put in the message text.</span></span> <span data-ttu-id="6d600-125">Outre <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contient une propriété nommée <xref:System.ArgumentException.ParamName%2A> dont la valeur doit être le nom de l’argument qui a provoqué la levée de l’exception.</span><span class="sxs-lookup"><span data-stu-id="6d600-125">In addition to <xref:System.Exception.Message%2A>, <xref:System.ArgumentException> contains a property named <xref:System.ArgumentException.ParamName%2A> that should be set to the name of the argument that caused the exception to be thrown.</span></span> <span data-ttu-id="6d600-126">Dans le cas d’une méthode setter de propriété, <xref:System.ArgumentException.ParamName%2A> doit être défini sur `value`.</span><span class="sxs-lookup"><span data-stu-id="6d600-126">In the case of a property setter, <xref:System.ArgumentException.ParamName%2A> should be set to `value`.</span></span>  
  
 <span data-ttu-id="6d600-127">Les membres de méthodes publiques et protégées doivent lever des exceptions dès qu’ils ne peuvent pas remplir leurs fonctions habituelles.</span><span class="sxs-lookup"><span data-stu-id="6d600-127">Public and protected methods members should throw exceptions whenever they cannot complete their intended functions.</span></span> <span data-ttu-id="6d600-128">La classe d’exception qui est levée doit être l’exception la plus spécifique disponible qui répond aux conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6d600-128">The exception class that is thrown should be the most specific exception available that fits the error conditions.</span></span> <span data-ttu-id="6d600-129">Ces exceptions doivent être documentées dans le cadre de la fonctionnalité de la classe. De plus, les classes dérivées ou les mises à jour de la classe d’origine doivent conserver le même comportement afin d’assurer la compatibilité descendante.</span><span class="sxs-lookup"><span data-stu-id="6d600-129">These exceptions should be documented as part of the class functionality, and derived classes or updates to the original class should retain the same behavior for backward compatibility.</span></span>  
  
## <a name="things-to-avoid-when-throwing-exceptions"></a><span data-ttu-id="6d600-130">Pratiques à éviter lors de la levée d’exceptions</span><span class="sxs-lookup"><span data-stu-id="6d600-130">Things to Avoid When Throwing Exceptions</span></span>  
 <span data-ttu-id="6d600-131">La liste suivante identifie les pratiques à éviter lors de la levée d’exceptions :</span><span class="sxs-lookup"><span data-stu-id="6d600-131">The following list identifies practices to avoid when throwing exceptions:</span></span>  
  
-   <span data-ttu-id="6d600-132">Les exceptions ne doivent pas être utilisées pour changer le flux d’un programme dans le cadre d’une exécution ordinaire.</span><span class="sxs-lookup"><span data-stu-id="6d600-132">Exceptions should not be used to change the flow of a program as part of ordinary execution.</span></span> <span data-ttu-id="6d600-133">Elles doivent être utilisées uniquement pour signaler et gérer les conditions d’erreur.</span><span class="sxs-lookup"><span data-stu-id="6d600-133">Exceptions should only be used to report and handle error conditions.</span></span>  
  
-   <span data-ttu-id="6d600-134">Les exceptions ne doivent pas être retournées comme valeur de retour ou paramètre au lieu d’être levées.</span><span class="sxs-lookup"><span data-stu-id="6d600-134">Exceptions should not be returned as a return value or parameter instead of being thrown.</span></span>  
  
-   <span data-ttu-id="6d600-135">Ne levez pas intentionnellement <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName> ni <xref:System.IndexOutOfRangeException?displayProperty=fullName> à partir de votre propre code source.</span><span class="sxs-lookup"><span data-stu-id="6d600-135">Do not throw <xref:System.Exception?displayProperty=fullName>, <xref:System.SystemException?displayProperty=fullName>, <xref:System.NullReferenceException?displayProperty=fullName>, or <xref:System.IndexOutOfRangeException?displayProperty=fullName> intentionally from your own source code.</span></span>  
  
-   <span data-ttu-id="6d600-136">Ne créez pas d’exceptions qui peuvent être levées en mode Debug mais pas en mode Release.</span><span class="sxs-lookup"><span data-stu-id="6d600-136">Do not create exceptions that can be thrown in debug mode but not release mode.</span></span> <span data-ttu-id="6d600-137">Pour identifier des erreurs d’exécution pendant la phase de développement, utilisez plutôt Debug Assert.</span><span class="sxs-lookup"><span data-stu-id="6d600-137">To identify run-time errors during the development phase, use Debug Assert instead.</span></span>  
  
## <a name="defining-exception-classes"></a><span data-ttu-id="6d600-138">Définition de classes d’exceptions</span><span class="sxs-lookup"><span data-stu-id="6d600-138">Defining Exception Classes</span></span>  
 <span data-ttu-id="6d600-139">Les programmes peuvent lever une classe d’exceptions prédéfinie dans l’espace de noms <xref:System> (sauf dans les endroits préalablement signalés) ou créer leurs propres classes d’exceptions en les dérivant d’<xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="6d600-139">Programs can throw a predefined exception class in the <xref:System> namespace (except where previously noted), or create their own exception classes by deriving from <xref:System.Exception>.</span></span> <span data-ttu-id="6d600-140">Les classes dérivées doivent définir au moins trois constructeurs : un constructeur par défaut, un qui définit la propriété du message et un qui définit à la fois la propriété <xref:System.Exception.Message%2A> et la propriété <xref:System.Exception.InnerException%2A>.</span><span class="sxs-lookup"><span data-stu-id="6d600-140">The derived classes should define at least four constructors: one default constructor, one that sets the message property, and one that sets both the <xref:System.Exception.Message%2A> and <xref:System.Exception.InnerException%2A> properties.</span></span> <span data-ttu-id="6d600-141">Le quatrième constructeur est utilisé pour sérialiser l’exception.</span><span class="sxs-lookup"><span data-stu-id="6d600-141">The fourth constructor is used to serialize the exception.</span></span> <span data-ttu-id="6d600-142">Les nouvelles classes d’exception doivent être sérialisables.</span><span class="sxs-lookup"><span data-stu-id="6d600-142">New exception classes should be serializable.</span></span> <span data-ttu-id="6d600-143">Exemple :</span><span class="sxs-lookup"><span data-stu-id="6d600-143">For example:</span></span>  
  
 <span data-ttu-id="6d600-144">[!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6d600-144">[!code-cs[csProgGuideExceptions#15](../../../csharp/programming-guide/exceptions/codesnippet/CSharp/creating-and-throwing-exceptions_4.cs)]</span></span>  
  
 <span data-ttu-id="6d600-145">Les nouvelles propriétés doivent être ajoutées à la classe d’exceptions uniquement quand les données qu’elles fournissent sont utiles à la résolution de l’exception.</span><span class="sxs-lookup"><span data-stu-id="6d600-145">New properties should only be added to the exception class when the data they provide is useful to resolving the exception.</span></span> <span data-ttu-id="6d600-146">Si de nouvelles propriétés sont ajoutées à la classe d’exceptions dérivée, la méthode `ToString()` doit être substituée pour retourner les informations ajoutées.</span><span class="sxs-lookup"><span data-stu-id="6d600-146">If new properties are added to the derived exception class, `ToString()` should be overridden to return the added information.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6d600-147">Spécification du langage C#</span><span class="sxs-lookup"><span data-stu-id="6d600-147">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6d600-148">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6d600-148">See Also</span></span>  
 <span data-ttu-id="6d600-149">[Guide de programmation C#](../../../csharp/programming-guide/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d600-149">[C# Programming Guide](../../../csharp/programming-guide/index.md) </span></span>  
 <span data-ttu-id="6d600-150">[Exceptions et gestion des exceptions](../../../csharp/programming-guide/exceptions/index.md) </span><span class="sxs-lookup"><span data-stu-id="6d600-150">[Exceptions and Exception Handling](../../../csharp/programming-guide/exceptions/index.md) </span></span>  
 <span data-ttu-id="6d600-151">[Hiérarchie des exceptions](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b) </span><span class="sxs-lookup"><span data-stu-id="6d600-151">[Exception Hierarchy](http://msdn.microsoft.com/library/f7d68675-be06-40fb-a555-05f0c5a6f66b) </span></span>  
 [<span data-ttu-id="6d600-152">Gestion des exceptions</span><span class="sxs-lookup"><span data-stu-id="6d600-152">Exception Handling</span></span>](../../../csharp/programming-guide/exceptions/exception-handling.md)


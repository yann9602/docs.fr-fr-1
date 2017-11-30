---
title: "Classe et propriétés d'exception"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- exceptions, Exception class
- Exception class
ms.assetid: e2e1f8c4-e7b4-467d-9a66-13c90861221d
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 253a9846e484aa4e54c3433b0bbc8623519bbb7e
ms.sourcegitcommit: bbde43da655ae7bea1977f7af7345eb87bd7fd5f
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2017
---
# <a name="exception-class-and-properties"></a><span data-ttu-id="ed988-102">Classe et propriétés d’exception</span><span class="sxs-lookup"><span data-stu-id="ed988-102">Exception class and properties</span></span>

<span data-ttu-id="ed988-103">La classe <xref:System.Exception> est la classe de base dont héritent les exceptions.</span><span class="sxs-lookup"><span data-stu-id="ed988-103">The <xref:System.Exception> class is the base class from which exceptions inherit.</span></span> <span data-ttu-id="ed988-104">Par exemple, la hiérarchie de classes <xref:System.InvalidCastException> se présente comme suit :</span><span class="sxs-lookup"><span data-stu-id="ed988-104">For example, the <xref:System.InvalidCastException> class hierarchy is as follows:</span></span>

```
Object
  Exception
    SystemException
       InvalidCastException
```

<span data-ttu-id="ed988-105">La classe <xref:System.Exception> a les propriétés suivantes qui vous permettront de mieux comprendre une exception.</span><span class="sxs-lookup"><span data-stu-id="ed988-105">The <xref:System.Exception> class has the following properties that help make understanding an exception easier.</span></span>

| <span data-ttu-id="ed988-106">Nom de propriété</span><span class="sxs-lookup"><span data-stu-id="ed988-106">Property Name</span></span> | <span data-ttu-id="ed988-107">Description</span><span class="sxs-lookup"><span data-stu-id="ed988-107">Description</span></span> |
| ------------- | ----------- |
| <xref:System.Exception.Data> | <span data-ttu-id="ed988-108"><xref:System.Collections.IDictionary> qui contient des données arbitraires dans des paires clé-valeur.</span><span class="sxs-lookup"><span data-stu-id="ed988-108">An <xref:System.Collections.IDictionary> that holds arbitrary data in key-value pairs.</span></span> |
| <xref:System.Exception.HelpLink> | <span data-ttu-id="ed988-109">Peut contenir une URL (ou URN) vers un fichier d’aide qui fournit des informations détaillées sur la cause d’une exception.</span><span class="sxs-lookup"><span data-stu-id="ed988-109">Can hold a URL (or URN) to a help file that provides extensive information about the cause of an exception.</span></span> |
| <xref:System.Exception.InnerException> | <span data-ttu-id="ed988-110">Cette propriété peut être utilisée pour créer et conserver une série d’exceptions pendant la gestion des exceptions.</span><span class="sxs-lookup"><span data-stu-id="ed988-110">This property can be used to create and preserve a series of exceptions during exception handling.</span></span> <span data-ttu-id="ed988-111">Vous pouvez l’utiliser pour créer une exception qui contient des exceptions interceptées précédemment.</span><span class="sxs-lookup"><span data-stu-id="ed988-111">You can use it to create a new exception that contains previously caught exceptions.</span></span> <span data-ttu-id="ed988-112">L’exception d’origine peut être capturée par la deuxième exception dans la propriété <xref:System.Exception.InnerException>, ce qui permet au code qui gère la deuxième exception d’examiner les informations supplémentaires.</span><span class="sxs-lookup"><span data-stu-id="ed988-112">The original exception can be captured by the second exception in the <xref:System.Exception.InnerException> property, allowing code that handles the second exception to examine the additional information.</span></span> <span data-ttu-id="ed988-113">Par exemple, supposons que vous disposez d’une méthode qui reçoit un argument avec une mise en forme incorrecte.</span><span class="sxs-lookup"><span data-stu-id="ed988-113">For example, suppose you have a method that receives an argument that's improperly formatted.</span></span>  <span data-ttu-id="ed988-114">Le code essaie de lire l’argument, mais une exception est levée.</span><span class="sxs-lookup"><span data-stu-id="ed988-114">The code tries to read the argument, but an exception is thrown.</span></span> <span data-ttu-id="ed988-115">La méthode intercepte l’exception et lève une exception <xref:System.FormatException>.</span><span class="sxs-lookup"><span data-stu-id="ed988-115">The method catches the exception and throws a <xref:System.FormatException>.</span></span> <span data-ttu-id="ed988-116">Pour améliorer la capacité de l’appelant à déterminer la raison pour laquelle une exception est levée, il est parfois souhaitable qu’une méthode intercepte une exception levée par une routine d’assistance, puis qu’elle lève une exception plus évocatrice de l’erreur qui s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ed988-116">To improve the caller's ability to determine the reason an exception is thrown, it is sometimes desirable for a method to catch an exception thrown by a helper routine and then throw an exception more indicative of the error that has occurred.</span></span> <span data-ttu-id="ed988-117">Une exception plus significative peut être créée, dans laquelle la référence à l’exception interne peut être définie sur l’exception d’origine.</span><span class="sxs-lookup"><span data-stu-id="ed988-117">A new and more meaningful exception can be created, where the inner exception reference can be set to the original exception.</span></span> <span data-ttu-id="ed988-118">Cette exception plus significative peut ensuite être levée pour l’appelant.</span><span class="sxs-lookup"><span data-stu-id="ed988-118">This more meaningful exception can then be thrown to the caller.</span></span> <span data-ttu-id="ed988-119">Notez que cette fonctionnalité vous permet de créer une série d’exceptions liées qui se termine avec l’exception initialement levée.</span><span class="sxs-lookup"><span data-stu-id="ed988-119">Note that with this functionality, you can create a series of linked exceptions that ends with the exception that was thrown first.</span></span> |
| <xref:System.Exception.Message> | <span data-ttu-id="ed988-120">Fournit les détails de la cause d’une exception.</span><span class="sxs-lookup"><span data-stu-id="ed988-120">Provides details about the cause of an exception.</span></span>
| <xref:System.Exception.Source> | <span data-ttu-id="ed988-121">Obtient ou définit le nom de l'application ou de l'objet qui est à l'origine de l'erreur.</span><span class="sxs-lookup"><span data-stu-id="ed988-121">Gets or sets the name of the application or the object that causes the error.</span></span> |
| <xref:System.Exception.StackTrace>| <span data-ttu-id="ed988-122">Contient une trace de pile qui peut être utilisée pour déterminer où une erreur s’est produite.</span><span class="sxs-lookup"><span data-stu-id="ed988-122">Contains a stack trace that can be used to determine where an error occurred.</span></span> <span data-ttu-id="ed988-123">La trace de la pile comprend le nom du fichier source et le numéro de ligne du programme si les informations de débogage sont disponibles.</span><span class="sxs-lookup"><span data-stu-id="ed988-123">The stack trace includes the source file name and program line number if debugging information is available.</span></span> |

<span data-ttu-id="ed988-124">La plupart des classes qui héritent de <xref:System.Exception> n’implémentent pas de membres supplémentaires ni ne fournissent de fonctionnalités supplémentaires, elles héritent simplement de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ed988-124">Most of the classes that inherit from <xref:System.Exception> do not implement additional members or provide additional functionality; they simply inherit from <xref:System.Exception>.</span></span> <span data-ttu-id="ed988-125">Par conséquent, vous pouvez trouver les informations les plus importantes d’une exception dans la hiérarchie des classes d’exception, le nom de l’exception et les informations contenues dans l’exception.</span><span class="sxs-lookup"><span data-stu-id="ed988-125">Therefore, the most important information for an exception can be found in the hierarchy of exception classes, the exception name, and the information contained in the exception.</span></span>

<span data-ttu-id="ed988-126">Nous vous recommandons de lever et intercepter uniquement des objets qui dérivent de <xref:System.Exception>, mais vous pouvez lever n’importe quel objet qui dérive de la <xref:System.Object> classe en tant qu’exception.</span><span class="sxs-lookup"><span data-stu-id="ed988-126">We recommend that you throw and catch only objects that derive from <xref:System.Exception>, but you can throw any object that derives from the <xref:System.Object> class as an exception.</span></span> <span data-ttu-id="ed988-127">Notez que tous les langages ne prennent pas forcément en charge la levée et l’interception d’objets qui ne dérivent pas de <xref:System.Exception>.</span><span class="sxs-lookup"><span data-stu-id="ed988-127">Note that not all languages support throwing and catching objects that do not derive from <xref:System.Exception>.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="ed988-128">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ed988-128">See Also</span></span>  
[<span data-ttu-id="ed988-129">Exceptions</span><span class="sxs-lookup"><span data-stu-id="ed988-129">Exceptions</span></span>](index.md)

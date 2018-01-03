---
title: "Comment : appeler des fonctions définies par modèle dans les requêtes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 6c804e4d-f348-4afd-9f63-d3f0f24bc6a9
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: d639297764333b99675cb9e076e816314f3567c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-call-model-defined-functions-in-queries"></a><span data-ttu-id="23ce6-102">Comment : appeler des fonctions définies par modèle dans les requêtes</span><span class="sxs-lookup"><span data-stu-id="23ce6-102">How to: Call Model-Defined Functions in Queries</span></span>
<span data-ttu-id="23ce6-103">Cette rubrique explique comment appeler des fonctions définies dans le modèle conceptuel à partir de requêtes [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce6-103">This topic describes how to call functions that are defined in the conceptual model from within [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] queries.</span></span>  
  
 <span data-ttu-id="23ce6-104">La procédure suivante fournit un plan de haut niveau pour appeler une fonction définie par modèle à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce6-104">The procedure below provides a high-level outline for calling a model-defined function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="23ce6-105">L'exemple qui suit fournit plus de détails sur les étapes de la procédure.</span><span class="sxs-lookup"><span data-stu-id="23ce6-105">The example that follows provides more detail about the steps in the procedure.</span></span> <span data-ttu-id="23ce6-106">La procédure suppose que vous avez défini une fonction dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="23ce6-106">The procedure assumes that you have defined a function in the conceptual model.</span></span> <span data-ttu-id="23ce6-107">Pour plus d’informations, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span><span class="sxs-lookup"><span data-stu-id="23ce6-107">For more information, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).</span></span>  
  
### <a name="to-call-a-function-defined-in-the-conceptual-model"></a><span data-ttu-id="23ce6-108">Pour appeler une fonction définie dans le modèle conceptuel</span><span class="sxs-lookup"><span data-stu-id="23ce6-108">To call a function defined in the conceptual model</span></span>  
  
1.  <span data-ttu-id="23ce6-109">Ajoutez une méthode CLR (Common Language Runtime) à votre application qui se mappe à la fonction définie dans le modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="23ce6-109">Add a common language runtime (CLR) method to your application that maps to the function defined in the conceptual model.</span></span> <span data-ttu-id="23ce6-110">Pour mapper la méthode, vous devez lui appliquer un attribut <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute>.</span><span class="sxs-lookup"><span data-stu-id="23ce6-110">To map the method, you must apply an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to the method.</span></span> <span data-ttu-id="23ce6-111">Notez que les paramètres <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> et <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> de l'attribut correspondent respectivement au nom de l'espace de noms du modèle conceptuel et au nom de la fonction du modèle conceptuel.</span><span class="sxs-lookup"><span data-stu-id="23ce6-111">Note that the <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.NamespaceName%2A> and <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute.FunctionName%2A> parameters of the attribute are the namespace name of the conceptual model and the function name in the conceptual model respectively.</span></span> <span data-ttu-id="23ce6-112">La résolution des noms de fonctions pour LINQ respecte la casse.</span><span class="sxs-lookup"><span data-stu-id="23ce6-112">Function name resolution for LINQ is case sensitive.</span></span>  
  
2.  <span data-ttu-id="23ce6-113">Appelez la fonction dans une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce6-113">Call the function in a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23ce6-114">Exemple</span><span class="sxs-lookup"><span data-stu-id="23ce6-114">Example</span></span>  
 <span data-ttu-id="23ce6-115">L'exemple suivant montre comment appeler une fonction définie dans le modèle conceptuel à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce6-115">The following example demonstrates how to call a function that is defined in the conceptual model from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="23ce6-116">L'exemple utilise le modèle School.</span><span class="sxs-lookup"><span data-stu-id="23ce6-116">The example uses the School model.</span></span> <span data-ttu-id="23ce6-117">Pour plus d’informations sur le modèle School, consultez [création de la base de données School](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) et [générer le fichier de .edmx scolaire](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span><span class="sxs-lookup"><span data-stu-id="23ce6-117">For information about the School model, see [Creating the School Sample Database](http://msdn.microsoft.com/en-us/c1bec483-a0ea-4660-aa0b-7b0a8b68fed0) and [Generating the School .edmx File](http://msdn.microsoft.com/en-us/c48b3907-a8be-4fe6-884c-e95af1852758).</span></span>  
  
 <span data-ttu-id="23ce6-118">La fonction de modèle conceptuel suivante retourne le nombre d'années écoulées depuis l'embauche d'un formateur.</span><span class="sxs-lookup"><span data-stu-id="23ce6-118">The following conceptual model function returns the number of years since an instructor was hired.</span></span> <span data-ttu-id="23ce6-119">Pour plus d’informations sur l’ajout de la fonction à un modèle conceptuel, consultez [Comment : définir des fonctions personnalisées dans le modèle conceptuel](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span><span class="sxs-lookup"><span data-stu-id="23ce6-119">For information about adding the function to a conceptual model, see [How to: Define Custom Functions in the Conceptual Model](http://msdn.microsoft.com/en-us/0dad7b8b-58f6-4271-b238-f34810d68e5f).)</span></span>  
  
 [!code-xml[DP ConceptualModelFunctions#1](../../../../../../samples/snippets/xml/VS_Snippets_Data/dp conceptualmodelfunctions/xml/school.edmx#1)]
  
## <a name="example"></a><span data-ttu-id="23ce6-120">Exemple</span><span class="sxs-lookup"><span data-stu-id="23ce6-120">Example</span></span>  
 <span data-ttu-id="23ce6-121">Ensuite, ajoutez la méthode suivante à votre application et utilisez un objet <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> pour la mapper à la fonction de modèle conceptuel :</span><span class="sxs-lookup"><span data-stu-id="23ce6-121">Next, add the following method to your application and use an <xref:System.Data.Objects.DataClasses.EdmFunctionAttribute> to map it to the conceptual model function:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#2)]
 [!code-vb[DP ConceptualModelFunctions#2](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#2)]  
  
## <a name="example"></a><span data-ttu-id="23ce6-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="23ce6-122">Example</span></span>  
 <span data-ttu-id="23ce6-123">Vous pouvez à présent appeler la fonction de modèle conceptuel à partir d'une requête [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)].</span><span class="sxs-lookup"><span data-stu-id="23ce6-123">Now you can call the conceptual model function from within a [!INCLUDE[linq_entities](../../../../../../includes/linq-entities-md.md)] query.</span></span> <span data-ttu-id="23ce6-124">Le code suivant appelle la méthode pour afficher tous les formateurs embauchés il y a plus de dix ans :</span><span class="sxs-lookup"><span data-stu-id="23ce6-124">The following code calls the method to display all instructors that were hired more than ten years ago:</span></span>  
  
 [!code-csharp[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/csharp/VS_Snippets_Data/dp conceptualmodelfunctions/cs/program.cs#3)]
 [!code-vb[DP ConceptualModelFunctions#3](../../../../../../samples/snippets/visualbasic/VS_Snippets_Data/dp conceptualmodelfunctions/vb/module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="23ce6-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23ce6-125">See Also</span></span>  
 [<span data-ttu-id="23ce6-126">vue d’ensemble du fichier .edmx</span><span class="sxs-lookup"><span data-stu-id="23ce6-126">.edmx File Overview</span></span>](http://msdn.microsoft.com/en-us/f4c8e7ce-1db6-417e-9759-15f8b55155d4)  
 [<span data-ttu-id="23ce6-127">Requêtes dans LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="23ce6-127">Queries in LINQ to Entities</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/queries-in-linq-to-entities.md)  
 [<span data-ttu-id="23ce6-128">Appel de fonctions dans les requêtes LINQ to Entities</span><span class="sxs-lookup"><span data-stu-id="23ce6-128">Calling Functions in LINQ to Entities Queries</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/calling-functions-in-linq-to-entities-queries.md)  
 [<span data-ttu-id="23ce6-129">Guide pratique pour appeler des fonctions définies par modèle comme méthodes d’objet</span><span class="sxs-lookup"><span data-stu-id="23ce6-129">How to: Call Model-Defined Functions as Object Methods</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/how-to-call-model-defined-functions-as-object-methods.md)

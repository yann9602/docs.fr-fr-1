---
title: "Écriture des attributs personnalisés"
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
- cpp
helpviewer_keywords:
- multiple attribute instances
- AttributeTargets enumeration
- attributes [.NET Framework], custom
- AllowMultiple property
- custom attributes
- AttributeUsageAttribute class, custom attributes
- Inherited property
- attribute classes, declaring
ms.assetid: 97216f69-bde8-49fd-ac40-f18c500ef5dc
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 0205edba221b833625becbe6a1f2fdda2f9409a2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="writing-custom-attributes"></a><span data-ttu-id="35e2b-102">Écriture des attributs personnalisés</span><span class="sxs-lookup"><span data-stu-id="35e2b-102">Writing Custom Attributes</span></span>
<span data-ttu-id="35e2b-103">Pour concevoir vos propres attributs personnalisés, vous n’avez pas besoin de maîtriser les nombreux nouveaux concepts.</span><span class="sxs-lookup"><span data-stu-id="35e2b-103">To design your own custom attributes, you do not need to master many new concepts.</span></span> <span data-ttu-id="35e2b-104">Si vous êtes familiarisé avec la programmation orientée objet et savez concevoir des classes, vous possédez déjà la plupart des connaissances nécessaires.</span><span class="sxs-lookup"><span data-stu-id="35e2b-104">If you are familiar with object-oriented programming and know how to design classes, you already have most of the knowledge needed.</span></span> <span data-ttu-id="35e2b-105">Attributs personnalisés sont essentiellement des classes traditionnelles qui dérivent directement ou indirectement de <xref:System.Attribute?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35e2b-105">Custom attributes are essentially traditional classes that derive directly or indirectly from <xref:System.Attribute?displayProperty=nameWithType>.</span></span> <span data-ttu-id="35e2b-106">Tout comme les classes traditionnelles, les attributs personnalisés contiennent des méthodes qui stockent et récupèrent les données.</span><span class="sxs-lookup"><span data-stu-id="35e2b-106">Just like traditional classes, custom attributes contain methods that store and retrieve data.</span></span>  
  
 <span data-ttu-id="35e2b-107">Les principales étapes permettant de concevoir correctement des classes d’attributs personnalisés sont les suivantes :</span><span class="sxs-lookup"><span data-stu-id="35e2b-107">The primary steps to properly design custom attribute classes are as follows:</span></span>  
  
-   [<span data-ttu-id="35e2b-108">Application d’AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="35e2b-108">Applying the AttributeUsageAttribute</span></span>](#cpconapplyingattributeusageattribute)  
  
-   [<span data-ttu-id="35e2b-109">Déclaration de la classe d’attributs</span><span class="sxs-lookup"><span data-stu-id="35e2b-109">Declaring the attribute class</span></span>](#cpcondeclaringattributeclass)  
  
-   [<span data-ttu-id="35e2b-110">Déclaration des constructeurs</span><span class="sxs-lookup"><span data-stu-id="35e2b-110">Declaring constructors</span></span>](#cpcondeclaringconstructors)  
  
-   [<span data-ttu-id="35e2b-111">Déclaration des propriétés</span><span class="sxs-lookup"><span data-stu-id="35e2b-111">Declaring properties</span></span>](#cpcondeclaringproperties)  
  
 <span data-ttu-id="35e2b-112">Cette section décrit chacune de ces étapes et se termine par un [exemple d’attribut personnalisé](#cpconcustomattributeexample).</span><span class="sxs-lookup"><span data-stu-id="35e2b-112">This section describes each of these steps and concludes with a [custom attribute example](#cpconcustomattributeexample).</span></span>  
  
<a name="cpconapplyingattributeusageattribute"></a>   
## <a name="applying-the-attributeusageattribute"></a><span data-ttu-id="35e2b-113">Application d’AttributeUsageAttribute</span><span class="sxs-lookup"><span data-stu-id="35e2b-113">Applying the AttributeUsageAttribute</span></span>  
 <span data-ttu-id="35e2b-114">Une déclaration d’attribut personnalisé commence par **AttributeUsageAttribute**, qui définit certaines caractéristiques clés de votre classe d’attributs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-114">A custom attribute declaration begins with the **AttributeUsageAttribute**, which defines some of the key characteristics of your attribute class.</span></span> <span data-ttu-id="35e2b-115">Par exemple, vous pouvez spécifier si votre attribut peut être hérité par d’autres classes ou spécifier les éléments auxquels l’attribut peut être appliqué.</span><span class="sxs-lookup"><span data-stu-id="35e2b-115">For example, you can specify whether your attribute can be inherited by other classes or specify which elements the attribute can be applied to.</span></span> <span data-ttu-id="35e2b-116">Le fragment de code suivant montre comment utiliser **AttributeUsageAttribute**.</span><span class="sxs-lookup"><span data-stu-id="35e2b-116">The following code fragment demonstrates how to use the **AttributeUsageAttribute**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#5](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#5)]
 [!code-csharp[Conceptual.Attributes.Usage#5](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#5)]
 [!code-vb[Conceptual.Attributes.Usage#5](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#5)]  
  
 <span data-ttu-id="35e2b-117">Le <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> a trois membres qui sont importants pour la création d’attributs personnalisés : [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), et [AllowMultiple](#cpconwritingcustomattributesanchor3).</span><span class="sxs-lookup"><span data-stu-id="35e2b-117">The <xref:System.AttributeUsageAttribute?displayProperty=nameWithType> has three members that are important for the creation of custom attributes: [AttributeTargets](#cpconwritingcustomattributesanchor1), [Inherited](#cpconwritingcustomattributesanchor2), and [AllowMultiple](#cpconwritingcustomattributesanchor3).</span></span>  
  
<a name="cpconwritingcustomattributesanchor1"></a>   
### <a name="attributetargets-member"></a><span data-ttu-id="35e2b-118">Membre AttributeTargets</span><span class="sxs-lookup"><span data-stu-id="35e2b-118">AttributeTargets Member</span></span>  
 <span data-ttu-id="35e2b-119">Dans l’exemple précédent, **AttributeTargets.All** est spécifié, ce qui indique que cet attribut peut être appliqué à tous les éléments de programme.</span><span class="sxs-lookup"><span data-stu-id="35e2b-119">In the previous example, **AttributeTargets.All** is specified, indicating that this attribute can be applied to all program elements.</span></span> <span data-ttu-id="35e2b-120">Vous pouvez également spécifier **AttributeTargets.Class**, qui indique que votre attribut peut être appliqué uniquement à une classe, ou **AttributeTargets.Method**, qui indique que votre attribut peut être appliqué uniquement à une méthode.</span><span class="sxs-lookup"><span data-stu-id="35e2b-120">Alternatively, you can specify **AttributeTargets.Class**, indicating that your attribute can be applied only to a class, or **AttributeTargets.Method**, indicating that your attribute can be applied only to a method.</span></span> <span data-ttu-id="35e2b-121">Tous les éléments de programme peuvent être marqués pour description par un attribut personnalisé de cette manière.</span><span class="sxs-lookup"><span data-stu-id="35e2b-121">All program elements can be marked for description by a custom attribute in this manner.</span></span>  
  
 <span data-ttu-id="35e2b-122">Vous pouvez également transmettre plusieurs instances de <xref:System.AttributeTargets>.</span><span class="sxs-lookup"><span data-stu-id="35e2b-122">You can also pass multiple instances of <xref:System.AttributeTargets>.</span></span> <span data-ttu-id="35e2b-123">Le fragment de code suivant spécifie qu’un attribut personnalisé peut être appliqué à n’importe quelle classe ou méthode.</span><span class="sxs-lookup"><span data-stu-id="35e2b-123">The following code fragment specifies that a custom attribute can be applied to any class or method.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#6](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#6)]
 [!code-csharp[Conceptual.Attributes.Usage#6](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#6)]
 [!code-vb[Conceptual.Attributes.Usage#6](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#6)]  
  
<a name="cpconwritingcustomattributesanchor2"></a>   
### <a name="inherited-property"></a><span data-ttu-id="35e2b-124">Propriété Inherited</span><span class="sxs-lookup"><span data-stu-id="35e2b-124">Inherited Property</span></span>  
 <span data-ttu-id="35e2b-125">Le <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> propriété indique si votre attribut peut être hérité par les classes qui sont dérivées des classes auxquelles votre attribut est appliqué.</span><span class="sxs-lookup"><span data-stu-id="35e2b-125">The <xref:System.AttributeUsageAttribute.Inherited%2A?displayProperty=nameWithType> property indicates whether your attribute can be inherited by classes that are derived from the classes to which your attribute is applied.</span></span> <span data-ttu-id="35e2b-126">Cette propriété reçoit un indicateur **true** (par défaut) ou **false** .</span><span class="sxs-lookup"><span data-stu-id="35e2b-126">This property takes either a **true** (the default) or **false** flag.</span></span> <span data-ttu-id="35e2b-127">Dans l’exemple suivant, la valeur `MyAttribute` par défaut de <xref:System.AttributeUsageAttribute.Inherited%2A> est **true**, tandis que la valeur `YourAttribute` de <xref:System.AttributeUsageAttribute.Inherited%2A> est **false**.</span><span class="sxs-lookup"><span data-stu-id="35e2b-127">For example, in the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.Inherited%2A> value of **true**, while `YourAttribute` has an <xref:System.AttributeUsageAttribute.Inherited%2A> value of **false**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#7](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#7)]
 [!code-csharp[Conceptual.Attributes.Usage#7](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#7)]
 [!code-vb[Conceptual.Attributes.Usage#7](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#7)]  
  
 <span data-ttu-id="35e2b-128">Les deux attributs sont ensuite appliqués à une méthode dans la classe de base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="35e2b-128">The two attributes are then applied to a method in the base class `MyClass`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#9](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#9)]
 [!code-csharp[Conceptual.Attributes.Usage#9](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#9)]
 [!code-vb[Conceptual.Attributes.Usage#9](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#9)]  
  
 <span data-ttu-id="35e2b-129">Enfin, la classe `YourClass` est héritée de la classe de base `MyClass`.</span><span class="sxs-lookup"><span data-stu-id="35e2b-129">Finally, the class `YourClass` is inherited from the base class `MyClass`.</span></span> <span data-ttu-id="35e2b-130">La méthode `MyMethod` affiche `MyAttribute`, mais pas `YourAttribute`.</span><span class="sxs-lookup"><span data-stu-id="35e2b-130">The method `MyMethod` shows `MyAttribute`, but not `YourAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#10](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#10)]
 [!code-csharp[Conceptual.Attributes.Usage#10](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#10)]
 [!code-vb[Conceptual.Attributes.Usage#10](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#10)]  
  
<a name="cpconwritingcustomattributesanchor3"></a>   
### <a name="allowmultiple-property"></a><span data-ttu-id="35e2b-131">Propriété AllowMultiple</span><span class="sxs-lookup"><span data-stu-id="35e2b-131">AllowMultiple Property</span></span>  
 <span data-ttu-id="35e2b-132">Le <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> propriété indique si plusieurs instances de votre attribut peuvent exister sur un élément.</span><span class="sxs-lookup"><span data-stu-id="35e2b-132">The <xref:System.AttributeUsageAttribute.AllowMultiple%2A?displayProperty=nameWithType> property indicates whether multiple instances of your attribute can exist on an element.</span></span> <span data-ttu-id="35e2b-133">Si la valeur est **true**, plusieurs instances sont autorisées, si la valeur est **false** (par défaut), une seule instance est autorisée.</span><span class="sxs-lookup"><span data-stu-id="35e2b-133">If set to **true**, multiple instances are allowed; if set to **false** (the default), only one instance is allowed.</span></span>  
  
 <span data-ttu-id="35e2b-134">Dans l’exemple suivant, la valeur `MyAttribute` par défaut de <xref:System.AttributeUsageAttribute.AllowMultiple%2A> est **true**, tandis que la valeur de `YourAttribute` est **false**.</span><span class="sxs-lookup"><span data-stu-id="35e2b-134">In the following example, `MyAttribute` has a default <xref:System.AttributeUsageAttribute.AllowMultiple%2A> value of **false**, while `YourAttribute` has a value of **true**.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#11](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#11)]
 [!code-csharp[Conceptual.Attributes.Usage#11](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#11)]
 [!code-vb[Conceptual.Attributes.Usage#11](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#11)]  
  
 <span data-ttu-id="35e2b-135">Quand plusieurs instances de ces attributs sont appliquées, `MyAttribute` génère une erreur du compilateur.</span><span class="sxs-lookup"><span data-stu-id="35e2b-135">When multiple instances of these attributes are applied, `MyAttribute` produces a compiler error.</span></span> <span data-ttu-id="35e2b-136">L’exemple de code suivant illustre l’utilisation valide de `YourAttribute` et l’utilisation non valide de `MyAttribute`.</span><span class="sxs-lookup"><span data-stu-id="35e2b-136">The following code example shows the valid use of `YourAttribute` and the invalid use of `MyAttribute`.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#13](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#13)]
 [!code-csharp[Conceptual.Attributes.Usage#13](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#13)]
 [!code-vb[Conceptual.Attributes.Usage#13](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#13)]  
  
 <span data-ttu-id="35e2b-137">Si la propriété <xref:System.AttributeUsageAttribute.AllowMultiple%2A> et la propriété <xref:System.AttributeUsageAttribute.Inherited%2A> ont la valeur **true**, une classe héritée d’une autre classe peut hériter d’un attribut et avoir une autre instance du même attribut appliquée dans la même classe enfant.</span><span class="sxs-lookup"><span data-stu-id="35e2b-137">If both the <xref:System.AttributeUsageAttribute.AllowMultiple%2A> property and the <xref:System.AttributeUsageAttribute.Inherited%2A> property are set to **true**, a class that is inherited from another class can inherit an attribute and have another instance of the same attribute applied in the same child class.</span></span> <span data-ttu-id="35e2b-138">Si <xref:System.AttributeUsageAttribute.AllowMultiple%2A> a la valeur **false**, les valeurs des attributs de la classe parente sont remplacées par les nouvelles instances du même attribut dans la classe enfant.</span><span class="sxs-lookup"><span data-stu-id="35e2b-138">If <xref:System.AttributeUsageAttribute.AllowMultiple%2A> is set to **false**, the values of any attributes in the parent class will be overwritten by new instances of the same attribute in the child class.</span></span>  
  
<a name="cpcondeclaringattributeclass"></a>   
## <a name="declaring-the-attribute-class"></a><span data-ttu-id="35e2b-139">Déclaration de la classe d’attributs</span><span class="sxs-lookup"><span data-stu-id="35e2b-139">Declaring the Attribute Class</span></span>  
 <span data-ttu-id="35e2b-140">Une fois que vous avez appliqué <xref:System.AttributeUsageAttribute>, vous pouvez commencer à définir les particularités de votre attribut.</span><span class="sxs-lookup"><span data-stu-id="35e2b-140">After you apply the <xref:System.AttributeUsageAttribute>, you can begin to define the specifics of your attribute.</span></span> <span data-ttu-id="35e2b-141">La déclaration d’une classe d’attributs ressemble à la déclaration d’une classe traditionnelle, comme illustré dans le code suivant.</span><span class="sxs-lookup"><span data-stu-id="35e2b-141">The declaration of an attribute class looks similar to the declaration of a traditional class, as demonstrated by the following code.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#14](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#14)]
 [!code-csharp[Conceptual.Attributes.Usage#14](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#14)]
 [!code-vb[Conceptual.Attributes.Usage#14](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#14)]  
  
 <span data-ttu-id="35e2b-142">Cette définition de l’attribut illustre les points suivants :</span><span class="sxs-lookup"><span data-stu-id="35e2b-142">This attribute definition demonstrates the following points:</span></span>  
  
-   <span data-ttu-id="35e2b-143">Les classes d’attributs doivent être déclarées comme des classes publiques.</span><span class="sxs-lookup"><span data-stu-id="35e2b-143">Attribute classes must be declared as public classes.</span></span>  
  
-   <span data-ttu-id="35e2b-144">Par convention, le nom de la classe d’attributs se termine par le mot **Attribute**.</span><span class="sxs-lookup"><span data-stu-id="35e2b-144">By convention, the name of the attribute class ends with the word **Attribute**.</span></span> <span data-ttu-id="35e2b-145">Même si elle n’est pas obligatoire, cette convention est recommandée pour une meilleure lisibilité.</span><span class="sxs-lookup"><span data-stu-id="35e2b-145">While not required, this convention is recommended for readability.</span></span> <span data-ttu-id="35e2b-146">Quand l’attribut est appliqué, l’inclusion du mot Attribute est facultative.</span><span class="sxs-lookup"><span data-stu-id="35e2b-146">When the attribute is applied, the inclusion of the word Attribute is optional.</span></span>  
  
-   <span data-ttu-id="35e2b-147">Toutes les classes d’attributs doivent hériter directement ou indirectement de **System.Attribute**.</span><span class="sxs-lookup"><span data-stu-id="35e2b-147">All attribute classes must inherit directly or indirectly from **System.Attribute**.</span></span>  
  
-   <span data-ttu-id="35e2b-148">Dans Microsoft Visual Basic, toutes les classes d’attributs personnalisés doivent avoir l’attribut **AttributeUsageAttribute** .</span><span class="sxs-lookup"><span data-stu-id="35e2b-148">In Microsoft Visual Basic, all custom attribute classes must have the **AttributeUsageAttribute** attribute.</span></span>  
  
<a name="cpcondeclaringconstructors"></a>   
## <a name="declaring-constructors"></a><span data-ttu-id="35e2b-149">Déclaration des constructeurs</span><span class="sxs-lookup"><span data-stu-id="35e2b-149">Declaring Constructors</span></span>  
 <span data-ttu-id="35e2b-150">Les attributs sont initialisés avec des constructeurs de la même façon que les classes traditionnelles.</span><span class="sxs-lookup"><span data-stu-id="35e2b-150">Attributes are initialized with constructors in the same way as traditional classes.</span></span> <span data-ttu-id="35e2b-151">Le fragment de code suivant illustre un constructeur d’attribut classique.</span><span class="sxs-lookup"><span data-stu-id="35e2b-151">The following code fragment illustrates a typical attribute constructor.</span></span> <span data-ttu-id="35e2b-152">Ce constructeur public accepte un paramètre et définit sa valeur sur une variable membre.</span><span class="sxs-lookup"><span data-stu-id="35e2b-152">This public constructor takes a parameter and sets its value equal to a member variable.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#15](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#15)]
 [!code-csharp[Conceptual.Attributes.Usage#15](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#15)]
 [!code-vb[Conceptual.Attributes.Usage#15](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#15)]  
  
 <span data-ttu-id="35e2b-153">Vous pouvez surcharger le constructeur pour qu’il reçoive différentes combinaisons de valeurs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-153">You can overload the constructor to accommodate different combinations of values.</span></span> <span data-ttu-id="35e2b-154">Si vous définissez également une [propriété](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) pour votre classe d’attributs personnalisés, vous pouvez utiliser une combinaison de paramètres nommés et positionnels lors de l’initialisation de l’attribut.</span><span class="sxs-lookup"><span data-stu-id="35e2b-154">If you also define a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52) for your custom attribute class, you can use a combination of named and positional parameters when initializing the attribute.</span></span> <span data-ttu-id="35e2b-155">En général, vous définissez tous les paramètres obligatoires comme des paramètres positionnels et tous les paramètres facultatifs comme des paramètres nommés.</span><span class="sxs-lookup"><span data-stu-id="35e2b-155">Typically, you define all required parameters as positional and all optional parameters as named.</span></span> <span data-ttu-id="35e2b-156">Dans ce cas, l’attribut ne peut pas être initialisé sans le paramètre obligatoire.</span><span class="sxs-lookup"><span data-stu-id="35e2b-156">In this case, the attribute cannot be initialized without the required parameter.</span></span> <span data-ttu-id="35e2b-157">Tous les autres paramètres sont facultatifs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-157">All other parameters are optional.</span></span> <span data-ttu-id="35e2b-158">Notez que dans Visual Basic, les constructeurs d’une classe d’attributs ne doivent pas utiliser d’argument ParamArray.</span><span class="sxs-lookup"><span data-stu-id="35e2b-158">Note that in Visual Basic, constructors for an attribute class should not use a ParamArray argument.</span></span>  
  
 <span data-ttu-id="35e2b-159">L’exemple de code suivant montre comment un attribut qui utilise le constructeur précédent peut être appliqué à l’aide de paramètres obligatoires et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-159">The following code example shows how an attribute that uses the previous constructor can be applied using optional and required parameters.</span></span> <span data-ttu-id="35e2b-160">Il suppose que l’attribut a une valeur booléenne obligatoire et une propriété de chaîne facultative.</span><span class="sxs-lookup"><span data-stu-id="35e2b-160">It assumes that the attribute has one required Boolean value and one optional string property.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#17](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#17)]
 [!code-csharp[Conceptual.Attributes.Usage#17](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#17)]
 [!code-vb[Conceptual.Attributes.Usage#17](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#17)]  
  
<a name="cpcondeclaringproperties"></a>   
## <a name="declaring-properties"></a><span data-ttu-id="35e2b-161">Déclaration des propriétés</span><span class="sxs-lookup"><span data-stu-id="35e2b-161">Declaring Properties</span></span>  
 <span data-ttu-id="35e2b-162">Si vous voulez définir un paramètre nommé ou fournir un moyen facile de retourner les valeurs stockées par votre attribut, déclarez une [propriété](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span><span class="sxs-lookup"><span data-stu-id="35e2b-162">If you want to define a named parameter or provide an easy way to return the values stored by your attribute, declare a [property](http://msdn.microsoft.com/library/8f1a1ff1-0f05-40e0-bfdf-80de8fff7d52).</span></span> <span data-ttu-id="35e2b-163">Les propriétés d’attribut doivent être déclarées comme des entités publiques avec une description du type de données à retourner.</span><span class="sxs-lookup"><span data-stu-id="35e2b-163">Attribute properties should be declared as public entities with a description of the data type that will be returned.</span></span> <span data-ttu-id="35e2b-164">Définissez la variable qui contient la valeur de votre propriété et associez-la aux méthodes **get** et **set** .</span><span class="sxs-lookup"><span data-stu-id="35e2b-164">Define the variable that will hold the value of your property and associate it with the **get** and **set** methods.</span></span> <span data-ttu-id="35e2b-165">L’exemple de code suivant montre comment implémenter une propriété simple dans votre attribut.</span><span class="sxs-lookup"><span data-stu-id="35e2b-165">The following code example demonstrates how to implement a simple property in your attribute.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#16](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#16)]
 [!code-csharp[Conceptual.Attributes.Usage#16](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#16)]
 [!code-vb[Conceptual.Attributes.Usage#16](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#16)]  
  
<a name="cpconcustomattributeexample"></a>   
## <a name="custom-attribute-example"></a><span data-ttu-id="35e2b-166">exemple d’attribut personnalisé</span><span class="sxs-lookup"><span data-stu-id="35e2b-166">Custom Attribute Example</span></span>  
 <span data-ttu-id="35e2b-167">Cette section intègre les informations précédentes et montre comment concevoir un attribut simple qui documente des informations sur l’auteur d’une section de code.</span><span class="sxs-lookup"><span data-stu-id="35e2b-167">This section incorporates the previous information and shows how to design a simple attribute that documents information about the author of a section of code.</span></span> <span data-ttu-id="35e2b-168">L’attribut de cet exemple stocke le nom et le niveau du programmeur, et indique si le code a été révisé.</span><span class="sxs-lookup"><span data-stu-id="35e2b-168">The attribute in this example stores the name and level of the programmer, and whether the code has been reviewed.</span></span> <span data-ttu-id="35e2b-169">Il utilise trois variables privées pour stocker les valeurs réelles à enregistrer.</span><span class="sxs-lookup"><span data-stu-id="35e2b-169">It uses three private variables to store the actual values to save.</span></span> <span data-ttu-id="35e2b-170">Chaque variable est représentée par une propriété publique qui obtient et définit les valeurs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-170">Each variable is represented by a public property that gets and sets the values.</span></span> <span data-ttu-id="35e2b-171">Enfin, le constructeur est défini avec deux paramètres obligatoires.</span><span class="sxs-lookup"><span data-stu-id="35e2b-171">Finally, the constructor is defined with two required parameters.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#4](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#4)]
 [!code-csharp[Conceptual.Attributes.Usage#4](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#4)]
 [!code-vb[Conceptual.Attributes.Usage#4](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#4)]  
  
 <span data-ttu-id="35e2b-172">Vous pouvez appliquer cet attribut à l’aide du nom complet, `DeveloperAttribute`, ou à l’aide du nom abrégé, `Developer`, de l’une des manières suivantes.</span><span class="sxs-lookup"><span data-stu-id="35e2b-172">You can apply this attribute using the full name, `DeveloperAttribute`, or using the abbreviated name, `Developer`, in one of the following ways.</span></span>  
  
 [!code-cpp[Conceptual.Attributes.Usage#12](../../../samples/snippets/cpp/VS_Snippets_CLR/conceptual.attributes.usage/cpp/source2.cpp#12)]
 [!code-csharp[Conceptual.Attributes.Usage#12](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.attributes.usage/cs/source2.cs#12)]
 [!code-vb[Conceptual.Attributes.Usage#12](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.attributes.usage/vb/source2.vb#12)]  
  
 <span data-ttu-id="35e2b-173">Le premier exemple montre l’attribut appliqué uniquement avec les paramètres nommés obligatoires, tandis que le deuxième exemple montre l’attribut appliqué avec les paramètres obligatoires et facultatifs.</span><span class="sxs-lookup"><span data-stu-id="35e2b-173">The first example shows the attribute applied with only the required named parameters, while the second example shows the attribute applied with both the required and optional parameters.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35e2b-174">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35e2b-174">See Also</span></span>  
 <xref:System.Attribute?displayProperty=nameWithType>  
 <xref:System.AttributeUsageAttribute>  
 [<span data-ttu-id="35e2b-175">Attributs</span><span class="sxs-lookup"><span data-stu-id="35e2b-175">Attributes</span></span>](../../../docs/standard/attributes/index.md)

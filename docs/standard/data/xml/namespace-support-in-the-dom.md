---
title: Prise en charge des espaces de noms dans le DOM
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f0548ead-0fed-41ee-b33e-117ba900d3bc
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 3145df6517df9db580bfcc5d67edd9d1a61f290b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="namespace-support-in-the-dom"></a><span data-ttu-id="a4ece-102">Prise en charge des espaces de noms dans le DOM</span><span class="sxs-lookup"><span data-stu-id="a4ece-102">Namespace Support in the DOM</span></span>
<span data-ttu-id="a4ece-103">Le DOM (Document Object Model ) XML gère parfaitement les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a4ece-103">The XML Document Object Model (DOM) is completely namespace-aware.</span></span> <span data-ttu-id="a4ece-104">Seuls les documents XML reconnaissant les espaces de noms sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="a4ece-104">Only namespace-aware XML documents are supported.</span></span> <span data-ttu-id="a4ece-105">Le World Wide Web Consortium (W3C) établit que les applications DOM implémentant le niveau 1 peuvent ne pas prendre en charge des espaces de noms, alors que les fonctionnalités du DOM de niveau 2 gèrent parfaitement les espaces de noms.</span><span class="sxs-lookup"><span data-stu-id="a4ece-105">The World Wide Web Consortium (W3C) specifies that DOM applications that implement Level 1 can be non-namespace-aware, and DOM Level 2 features are namespace-aware.</span></span> <span data-ttu-id="a4ece-106">Cependant, toutes les fonctionnalités du DOM XML tiennent compte des espaces de noms, peu importe si la méthode émane de la recommandation Document Object Model (DOM) de niveau 1 ou de niveau 2.</span><span class="sxs-lookup"><span data-stu-id="a4ece-106">However, all features in the XML DOM are namespace-aware, regardless if the method is from the Level 1 or Level 2 DOM Recommendation.</span></span>  
  
 <span data-ttu-id="a4ece-107">Par exemple, dans un environnement ne prenant pas en charge les espaces de noms, l'appel de `setAttribute("A:b", "123")` conformément à la recommandation Document Object Model (DOM) de niveau 1 ne donne pas pour résultat un attribut doté du préfixe `A` et du nom local `b`.</span><span class="sxs-lookup"><span data-stu-id="a4ece-107">For example, in a non-namespace-aware setting, calling `setAttribute("A:b", "123")`, as specified in the DOM Level 1 Recommendation, does not result in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="a4ece-108">Il produit un attribut dont la valeur est `A:b`.</span><span class="sxs-lookup"><span data-stu-id="a4ece-108">It would result in an attribute with the value `A:b`.</span></span>  
  
 <span data-ttu-id="a4ece-109">Dans un environnement prenant en charge les espaces de noms, par contre, l'appel à `setAttribute("A:b", "123")` de la recommandation Document Object Model (DOM) de niveau 2 génère un attribut dont le préfixe est `A` et le nom local, `b`.</span><span class="sxs-lookup"><span data-stu-id="a4ece-109">In a namespace-aware environment, the call to the DOM Level 2 `setAttribute("A:b", "123")` results in an attribute with a prefix of `A` and a local name of `b`.</span></span> <span data-ttu-id="a4ece-110">Voici comment Microsoft .NET Framework DOM fonctionne.</span><span class="sxs-lookup"><span data-stu-id="a4ece-110">This is how the Microsoft .NET Framework DOM works.</span></span>  
  
 <span data-ttu-id="a4ece-111">C'est pourquoi, toutes les méthodes qui prennent un paramètre de nom prennent également un préfixe destiné à qualifier ce nom.</span><span class="sxs-lookup"><span data-stu-id="a4ece-111">Therefore, for all methods that take a name parameter, these methods also take a prefix to qualify the name.</span></span> <span data-ttu-id="a4ece-112">Le paramètre de nom, tel que le `A:b` dans les **setAttribute** DOM Level 1 (méthode), est analysé comme suit :</span><span class="sxs-lookup"><span data-stu-id="a4ece-112">The name parameter, such as the `A:b` in the **setAttribute** DOM Level 1 method, is parsed as follows:</span></span>  
  
-   <span data-ttu-id="a4ece-113">En l'absence de caractère deux-points (:), le nom local correspond à la valeur du paramètre `name`, le préfixe et NamespaceURI étant des chaînes vides.</span><span class="sxs-lookup"><span data-stu-id="a4ece-113">If there are no colon (:) characters, then the local name is set to the `name` parameter, and the prefix and NamespaceURI are empty strings.</span></span>  
  
-   <span data-ttu-id="a4ece-114">En présence d'un caractère deux-points, le nom est scindé en deux parties au niveau de la position du premier caractère deux-points.</span><span class="sxs-lookup"><span data-stu-id="a4ece-114">If a colon is found, then the name is split into two parts based on the position of the first colon character.</span></span> <span data-ttu-id="a4ece-115">Le préfixe a la valeur de la chaîne se trouvant avant le deux-points, et le nom local est la chaîne située après ce caractère.</span><span class="sxs-lookup"><span data-stu-id="a4ece-115">The prefix is set to the string found before the colon, and local name is set to the string found after the colon.</span></span> <span data-ttu-id="a4ece-116">Pour les méthodes ne prenant pas de valeur NamespaceURI, NamespaceURI n'est pas résolu et garde comme valeur une chaîne vide.</span><span class="sxs-lookup"><span data-stu-id="a4ece-116">For methods that do not take a NamespaceURI value, the NamespaceURI is not resolved and remains set to empty string.</span></span> <span data-ttu-id="a4ece-117">Sinon, NamespaceURI a pour valeur la chaîne passée à la méthode.</span><span class="sxs-lookup"><span data-stu-id="a4ece-117">Otherwise, the NamespaceURI is set to the string passed to the method.</span></span> <span data-ttu-id="a4ece-118">Si le préfixe n’est pas défini, le **enregistrer** (méthode) et **InnerXml** et **OuterXml** propriétés échouent.</span><span class="sxs-lookup"><span data-stu-id="a4ece-118">If the prefix is undefined, then the **Save** method and **InnerXml** and **OuterXml** properties fail.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4ece-119">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="a4ece-119">See Also</span></span>  
 [<span data-ttu-id="a4ece-120">Document Object Model (DOM) XML</span><span class="sxs-lookup"><span data-stu-id="a4ece-120">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)

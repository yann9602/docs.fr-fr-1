---
title: "Portée des espaces de noms par défaut dans Visual Basic | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- VB
ms.assetid: d4cce80c-342f-4097-be8b-40ab0bfa90ba
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 138115cb1a5ec2e2c513419a32a9ebaec9c90d61
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017


---
# <a name="scope-of-default-namespaces-in-visual-basic"></a><span data-ttu-id="67758-102">Portée des espaces de noms par défaut dans Visual Basic</span><span class="sxs-lookup"><span data-stu-id="67758-102">Scope of Default Namespaces in Visual Basic</span></span>
<span data-ttu-id="67758-103">Les espaces de noms tels que représentés dans l'arborescence XML par défaut ne sont pas dans la portée pour les requêtes.</span><span class="sxs-lookup"><span data-stu-id="67758-103">Default namespaces as represented in the XML tree are not in scope for queries.</span></span> <span data-ttu-id="67758-104">Si vous avez le code XML qui est dans un espace de noms par défaut, vous devez déclarer une <xref:System.Xml.Linq.XNamespace>variable et de les combiner avec le nom local pour créer un nom complet à utiliser dans la requête.</xref:System.Xml.Linq.XNamespace></span><span class="sxs-lookup"><span data-stu-id="67758-104">If you have XML that is in a default namespace, you still must declare an <xref:System.Xml.Linq.XNamespace> variable, and combine it with the local name to make a qualified name to be used in the query.</span></span>  
  
 <span data-ttu-id="67758-105">L'un des problèmes les plus courants lors de l'interrogation d'une arborescence XML est que si celle-ci possède un espace de noms par défaut, le développeur écrit parfois la requête comme si le code XML n'était dans aucun espace de noms.</span><span class="sxs-lookup"><span data-stu-id="67758-105">One of the most common problems when querying XML trees is that if the XML tree has a default namespace, the developer sometimes writes the query as though the XML were not in a namespace.</span></span>  
  
 <span data-ttu-id="67758-106">Le premier ensemble d'exemples de cette rubrique illustre le chargement de code XML dans un espace de noms par défaut, mais son interrogation est incorrecte.</span><span class="sxs-lookup"><span data-stu-id="67758-106">The first set of examples in this topic shows a typical way that XML in a default namespace is loaded, but is queried improperly.</span></span>  
  
 <span data-ttu-id="67758-107">Le deuxième ensemble d'exemples illustre les corrections que vous devez apporter pour pouvoir interroger du code XML dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="67758-107">The second set of examples show the necessary corrections so that you can query XML in a namespace.</span></span>  
  
## <a name="example"></a><span data-ttu-id="67758-108">Exemple</span><span class="sxs-lookup"><span data-stu-id="67758-108">Example</span></span>  
 <span data-ttu-id="67758-109">Cet exemple illustre la création de code XML dans un espace de noms et une requête qui retourne un jeu de résultats vide.</span><span class="sxs-lookup"><span data-stu-id="67758-109">This example shows the creation of XML in a namespace, and a query that returns an empty result set.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67758-110">Code</span><span class="sxs-lookup"><span data-stu-id="67758-110">Code</span></span>  
  
```vb  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(CInt(el))  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="67758-111">Commentaires</span><span class="sxs-lookup"><span data-stu-id="67758-111">Comments</span></span>  
 <span data-ttu-id="67758-112">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="67758-112">This example produces the following result:</span></span>  
  
```  
Result set follows:  
End of result set  
```  
  
## <a name="example"></a><span data-ttu-id="67758-113">Exemple</span><span class="sxs-lookup"><span data-stu-id="67758-113">Example</span></span>  
 <span data-ttu-id="67758-114">Cet exemple illustre la création de code XML dans un espace de noms et une requête codée correctement.</span><span class="sxs-lookup"><span data-stu-id="67758-114">This example shows the creation of XML in a namespace, and a query that is coded properly.</span></span>  
  
 <span data-ttu-id="67758-115">Contrairement à l’exemple de code incorrect ci-dessus, l’approche correcte lors de l’utilisation de Visual Basic consiste à déclarer et initialiser un espace de noms global par défaut.</span><span class="sxs-lookup"><span data-stu-id="67758-115">In contrast to the incorrectly coded example above, the correct approach when using Visual Basic is to declare and initialize a global default namespace.</span></span> <span data-ttu-id="67758-116">Cela place toutes les propriétés XML dans l'espace de noms par défaut.</span><span class="sxs-lookup"><span data-stu-id="67758-116">This places all XML properties in the default namespace.</span></span> <span data-ttu-id="67758-117">Aucune autre modification n'est nécessaire pour que l'exemple fonctionne correctement.</span><span class="sxs-lookup"><span data-stu-id="67758-117">No other modifications are required to the example to make it work properly.</span></span>  
  
### <a name="code"></a><span data-ttu-id="67758-118">Code</span><span class="sxs-lookup"><span data-stu-id="67758-118">Code</span></span>  
  
```vb  
Imports <xmlns="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim root As XElement = _  
            <Root xmlns='http://www.adventure-works.com'>  
                <Child>1</Child>  
                <Child>2</Child>  
                <Child>3</Child>  
                <AnotherChild>4</AnotherChild>  
                <AnotherChild>5</AnotherChild>  
                <AnotherChild>6</AnotherChild>  
            </Root>  
        Dim c1 As IEnumerable(Of XElement) = _  
                From el In root.<Child> _  
                Select el  
        Console.WriteLine("Result set follows:")  
        For Each el As XElement In c1  
            Console.WriteLine(el.Value)  
        Next  
        Console.WriteLine("End of result set")  
    End Sub  
End Module  
```  
  
### <a name="comments"></a><span data-ttu-id="67758-119">Commentaires</span><span class="sxs-lookup"><span data-stu-id="67758-119">Comments</span></span>  
 <span data-ttu-id="67758-120">Cet exemple génère le résultat suivant :</span><span class="sxs-lookup"><span data-stu-id="67758-120">This example produces the following result:</span></span>  
  
```  
Result set follows:  
1  
2  
3  
End of result set  
```  
  
## <a name="see-also"></a><span data-ttu-id="67758-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="67758-121">See Also</span></span>  
 [<span data-ttu-id="67758-122">Utilisation des espaces de noms XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="67758-122">Working with XML Namespaces (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md)

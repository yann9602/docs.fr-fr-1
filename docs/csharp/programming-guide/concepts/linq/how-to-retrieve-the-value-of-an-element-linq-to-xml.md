---
title: "Guide pratique pour récupérer la valeur d’un élément (LINQ to XML) (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 4228c007-07c9-4cf2-a45b-e7074c109581
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ceb803eff68f72378ca195120ed96990d62d3593
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-value-of-an-element-linq-to-xml-c"></a><span data-ttu-id="0cbf5-102">Guide pratique pour récupérer la valeur d’un élément (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0cbf5-102">How to: Retrieve the Value of an Element (LINQ to XML) (C#)</span></span>
<span data-ttu-id="0cbf5-103">Cette rubrique montre comment obtenir la valeur d'éléments.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-103">This topic shows how to get the value of elements.</span></span> <span data-ttu-id="0cbf5-104">Il existe deux façons de procéder.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-104">There are two main ways to do this.</span></span> <span data-ttu-id="0cbf5-105">L'un des moyens consiste à convertir un objet <xref:System.Xml.Linq.XElement> ou <xref:System.Xml.Linq.XAttribute> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-105">One way is to cast an <xref:System.Xml.Linq.XElement> or an <xref:System.Xml.Linq.XAttribute> to the desired type.</span></span> <span data-ttu-id="0cbf5-106">L'opérateur de conversion explicite convertit alors le contenu de l'élément ou attribut vers le type spécifié et l'affecte à votre variable.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-106">The explicit conversion operator then converts the contents of the element or attribute to the specified type and assigns it to your variable.</span></span> <span data-ttu-id="0cbf5-107">En guise d'alternative, vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> ou <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-107">Alternatively, you can use the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property or the <xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
 <span data-ttu-id="0cbf5-108">Avec C#, toutefois, la conversion est généralement la meilleure approche.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-108">With C#, however, casting is generally the better approach.</span></span> <span data-ttu-id="0cbf5-109">Si vous convertissez l'élément ou attributs vers un type Nullable, le code est plus simple à écrire lors de la récupération de la valeur d'un élément (attribut) qui peut exister ou ne pas exister.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-109">If you cast the element or attribute to a nullable type, the code is simpler to write when retrieving the value of an element (or attribute) that might or might not exist.</span></span> <span data-ttu-id="0cbf5-110">Ceci est illustré dans le dernier exemple de cette rubrique.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-110">The last example in this topic demonstrates this.</span></span> <span data-ttu-id="0cbf5-111">Toutefois, vous ne pouvez pas définir le contenu d'un élément par le biais de la conversion, comme vous le pouvez par le biais de la propriété <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-111">However, you cannot set the contents of an element through casting, as you can through <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cbf5-112">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cbf5-112">Example</span></span>  
 <span data-ttu-id="0cbf5-113">Pour récupérer la valeur d'un élément, il vous suffit de convertir l'objet <xref:System.Xml.Linq.XElement> vers le type souhaité.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-113">To retrieve the value of an element, you just cast the <xref:System.Xml.Linq.XElement> object to your desired type.</span></span> <span data-ttu-id="0cbf5-114">Vous pouvez toujours convertir un élément en chaîne, comme suit :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-114">You can always cast an element to a string, as follows:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (string)e);  
```  
  
 <span data-ttu-id="0cbf5-115">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-115">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0cbf5-116">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cbf5-116">Example</span></span>  
 <span data-ttu-id="0cbf5-117">Vous pouvez également convertir des éléments vers des types autres que des chaînes.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-117">You can also cast elements to types other than string.</span></span> <span data-ttu-id="0cbf5-118">Par exemple, si vous avez un élément qui contient un entier, vous pouvez le convertir en `int`, comme illustré dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-118">For example, if you have an element that contains an integer, you can cast it to `int`, as shown in the following code:</span></span>  
  
```csharp  
XElement e = new XElement("Age", "44");  
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + (int)e);  
```  
  
 <span data-ttu-id="0cbf5-119">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-119">This example produces the following output:</span></span>  
  
```  
<Age>44</Age>  
Value of e:44  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0cbf5-120"> fournit des opérateurs de cast explicites pour les types de données suivants : `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID` et `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-120"> provides explicit cast operators for the following data types: `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="0cbf5-121"> fournit les mêmes opérateurs de conversion pour les objets <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-121"> provides the same cast operators for <xref:System.Xml.Linq.XAttribute> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0cbf5-122">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cbf5-122">Example</span></span>  
 <span data-ttu-id="0cbf5-123">Vous pouvez utiliser la propriété <xref:System.Xml.Linq.XElement.Value%2A> pour récupérer le contenu d'un élément :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-123">You can use the <xref:System.Xml.Linq.XElement.Value%2A> property to retrieve the contents of an element:</span></span>  
  
```csharp  
XElement e = new XElement("StringElement", "abcde");   
Console.WriteLine(e);  
Console.WriteLine("Value of e:" + e.Value);  
```  
  
 <span data-ttu-id="0cbf5-124">Cet exemple génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-124">This example produces the following output:</span></span>  
  
```  
<StringElement>abcde</StringElement>  
Value of e:abcde  
```  
  
## <a name="example"></a><span data-ttu-id="0cbf5-125">Exemple</span><span class="sxs-lookup"><span data-stu-id="0cbf5-125">Example</span></span>  
 <span data-ttu-id="0cbf5-126">Parfois, vous souhaitez récupérer la valeur d'un élément sans être certain qu'il existe.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-126">Sometimes you try to retrieve the value of an element even though you are not sure it exists.</span></span> <span data-ttu-id="0cbf5-127">Dans ce cas, lorsque vous assignez l’élément casté à un type Nullable (`string` ou l’un des types Nullable du [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), si l’élément n’existe pas, la variable assignée est définie sur `null`.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-127">In this case, when you assign the casted element to a nullable type (either `string` or one of the nullable types in the [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)]), if the element does not exist the assigned variable is just set to `null`.</span></span> <span data-ttu-id="0cbf5-128">Le code suivant montre que lorsqu'il n'est pas certain que l'élément existe, il est plus simple d'utiliser la conversion que la propriété <xref:System.Xml.Linq.XElement.Value%2A>.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-128">The following code shows that when the element might or might not exist, it is easier to use casting than to use the <xref:System.Xml.Linq.XElement.Value%2A> property.</span></span>  
  
```csharp  
XElement root = new XElement("Root",  
    new XElement("Child1", "child 1 content"),  
    new XElement("Child2", "2")  
);  
  
// The following assignments show why it is easier to use  
// casting when the element might or might not exist.  
  
string c1 = (string)root.Element("Child1");  
Console.WriteLine("c1:{0}", c1 == null ? "element does not exist" : c1);  
  
int? c2 = (int?)root.Element("Child2");  
Console.WriteLine("c2:{0}", c2 == null ? "element does not exist" : c2.ToString());  
  
string c3 = (string)root.Element("Child3");  
Console.WriteLine("c3:{0}", c3 == null ? "element does not exist" : c3);  
  
int? c4 = (int?)root.Element("Child4");  
Console.WriteLine("c4:{0}", c4 == null ? "element does not exist" : c4.ToString());  
  
Console.WriteLine();  
  
// The following assignments show the required code when using  
// the Value property when the element might or might not exist.  
// Notice that this is more difficult than the casting approach.  
  
XElement e1 = root.Element("Child1");  
string v1;  
if (e1 == null)  
    v1 = null;  
else  
    v1 = e1.Value;  
Console.WriteLine("v1:{0}", v1 == null ? "element does not exist" : v1);  
  
XElement e2 = root.Element("Child2");  
int? v2;  
if (e2 == null)  
    v2 = null;  
else  
    v2 = Int32.Parse(e2.Value);  
Console.WriteLine("v2:{0}", v2 == null ? "element does not exist" : v2.ToString());  
  
XElement e3 = root.Element("Child3");  
string v3;  
if (e3 == null)  
    v3 = null;  
else  
    v3 = e3.Value;  
Console.WriteLine("v3:{0}", v3 == null ? "element does not exist" : v3);  
  
XElement e4 = root.Element("Child4");  
int? v4;  
if (e4 == null)  
    v4 = null;  
else  
    v4 = Int32.Parse(e4.Value);  
Console.WriteLine("v4:{0}", v4 == null ? "element does not exist" : v4.ToString());  
```  
  
 <span data-ttu-id="0cbf5-129">Ce code génère la sortie suivante :</span><span class="sxs-lookup"><span data-stu-id="0cbf5-129">This code produces the following output:</span></span>  
  
```  
c1:child 1 content  
c2:2  
c3:element does not exist  
c4:element does not exist  
  
v1:child 1 content  
v2:2  
v3:element does not exist  
v4:element does not exist  
```  
  
 <span data-ttu-id="0cbf5-130">En général, le code à écrire est plus simple lors de l'utilisation de la conversion pour récupérer le contenu d'éléments ou d'attributs.</span><span class="sxs-lookup"><span data-stu-id="0cbf5-130">In general, you can write simpler code when using casting to retrieve the contents of elements and attributes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0cbf5-131">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="0cbf5-131">See Also</span></span>  
 [<span data-ttu-id="0cbf5-132">Axes LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0cbf5-132">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)

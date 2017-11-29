---
title: "Exemple de fichier XML : Données numériques dans un espace de noms3"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 51750cab-3c66-4511-90fb-b9d211308d31
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2437f22c1c76d1a24883cc2ed5b0e9c5f068e55b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/18/2017
---
# <a name="sample-xml-file-numerical-data-in-a-namespace"></a><span data-ttu-id="09d64-102">Exemple de fichier XML : Données numériques dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="09d64-102">Sample XML File: Numerical Data in a Namespace</span></span>
<span data-ttu-id="09d64-103">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09d64-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="09d64-104">Ce fichier contient des données numériques pour effectuer des additions, des moyennes et des regroupements.</span><span class="sxs-lookup"><span data-stu-id="09d64-104">This file contains numerical data for summing, averaging, and grouping.</span></span> <span data-ttu-id="09d64-105">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="09d64-105">The XML is in a namespace.</span></span>  
  
## <a name="data"></a><span data-ttu-id="09d64-106">Données</span><span class="sxs-lookup"><span data-stu-id="09d64-106">Data</span></span>  
  
```xml  
<Root xmlns='http://www.adatum.com'>  
  <TaxRate>7.25</TaxRate>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>24.50</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>1</Quantity>  
    <Price>89.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>5</Quantity>  
    <Price>4.95</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>3</Quantity>  
    <Price>66.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>10</Quantity>  
    <Price>.99</Price>  
  </Data>  
  <Data>  
    <Category>A</Category>  
    <Quantity>15</Quantity>  
    <Price>29.00</Price>  
  </Data>  
  <Data>  
    <Category>B</Category>  
    <Quantity>8</Quantity>  
    <Price>6.99</Price>  
  </Data>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="09d64-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="09d64-107">See Also</span></span>  
 [<span data-ttu-id="09d64-108">Exemples de documents XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="09d64-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)

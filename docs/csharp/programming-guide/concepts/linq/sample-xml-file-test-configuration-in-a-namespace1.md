---
title: "Exemple de fichier XML : Configuration de test dans un espace de noms1"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: e75ad1bc-5636-4623-9a34-a286a8c485d6
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 891616a9327add5671b512cf2d437f61cce947e7
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="26c75-102">Exemple de fichier XML : Configuration de test dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="26c75-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="26c75-103">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)].</span><span class="sxs-lookup"><span data-stu-id="26c75-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] documentation.</span></span> <span data-ttu-id="26c75-104">Il s'agit d'un fichier de configuration test.</span><span class="sxs-lookup"><span data-stu-id="26c75-104">This is a test configuration file.</span></span> <span data-ttu-id="26c75-105">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="26c75-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="26c75-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="26c75-106">TestConfigInNamespace.xml</span></span>  
  
```xml  
<?xml version="1.0"?>  
<Tests xmlns="http://www.adatum.com">  
  <Test TestId="0001" TestType="CMD">  
    <Name>Convert number to string</Name>  
    <CommandLine>Examp1.EXE</CommandLine>  
    <Input>1</Input>  
    <Output>One</Output>  
  </Test>  
  <Test TestId="0002" TestType="CMD">  
    <Name>Find succeeding characters</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>abc</Input>  
    <Output>def</Output>  
  </Test>  
  <Test TestId="0003" TestType="GUI">  
    <Name>Convert multiple numbers to strings</Name>  
    <CommandLine>Examp2.EXE /Verbose</CommandLine>  
    <Input>123</Input>  
    <Output>One Two Three</Output>  
  </Test>  
  <Test TestId="0004" TestType="GUI">  
    <Name>Find correlated key</Name>  
    <CommandLine>Examp3.EXE</CommandLine>  
    <Input>a1</Input>  
    <Output>b1</Output>  
  </Test>  
  <Test TestId="0005" TestType="GUI">  
    <Name>Count characters</Name>  
    <CommandLine>FinalExamp.EXE</CommandLine>  
    <Input>This is a test</Input>  
    <Output>14</Output>  
  </Test>  
  <Test TestId="0006" TestType="GUI">  
    <Name>Another Test</Name>  
    <CommandLine>Examp2.EXE</CommandLine>  
    <Input>Test Input</Input>  
    <Output>10</Output>  
  </Test>  
</Tests>  
```  
  
## <a name="see-also"></a><span data-ttu-id="26c75-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="26c75-107">See Also</span></span>  
 [<span data-ttu-id="26c75-108">Exemples de documents XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="26c75-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../csharp/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)


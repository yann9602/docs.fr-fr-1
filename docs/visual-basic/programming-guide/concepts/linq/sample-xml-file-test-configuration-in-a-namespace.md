---
title: "Exemple de fichier XML : Configuration de Test dans un Namespace3 | Documents Microsoft"
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
ms.assetid: aff02614-30ee-45e1-bc0f-d64b193d20b8
caps.latest.revision: 5
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 93a32c80e29d5b78bb4787f5528e3c9ed4bed20e
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="sample-xml-file-test-configuration-in-a-namespace"></a><span data-ttu-id="b7ed9-102">Exemple de fichier XML : Configuration test dans un espace de noms</span><span class="sxs-lookup"><span data-stu-id="b7ed9-102">Sample XML File: Test Configuration in a Namespace</span></span>
<span data-ttu-id="b7ed9-103">Le fichier XML suivant est utilisé dans différents exemples dans la documentation [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)].</span><span class="sxs-lookup"><span data-stu-id="b7ed9-103">The following XML file is used in various examples in the [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] documentation.</span></span> <span data-ttu-id="b7ed9-104">Il s'agit d'un fichier de configuration test.</span><span class="sxs-lookup"><span data-stu-id="b7ed9-104">This is a test configuration file.</span></span> <span data-ttu-id="b7ed9-105">Le code XML se trouve dans un espace de noms.</span><span class="sxs-lookup"><span data-stu-id="b7ed9-105">The XML is in a namespace.</span></span>  
  
## <a name="testconfiginnamespacexml"></a><span data-ttu-id="b7ed9-106">TestConfigInNamespace.xml</span><span class="sxs-lookup"><span data-stu-id="b7ed9-106">TestConfigInNamespace.xml</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b7ed9-107">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="b7ed9-107">See Also</span></span>  
 [<span data-ttu-id="b7ed9-108">Exemples de documents XML (LINQ to XML)</span><span class="sxs-lookup"><span data-stu-id="b7ed9-108">Sample XML Documents (LINQ to XML)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-documents-linq-to-xml.md)

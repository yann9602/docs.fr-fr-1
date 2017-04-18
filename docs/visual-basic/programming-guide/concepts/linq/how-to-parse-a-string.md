---
title: "Comment : analyser une chaîne (Visual Basic) | Documents Microsoft"
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
ms.assetid: 896e1b4b-f9bd-4975-8bc1-55b6badce1ac
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d062efd2e207f5db39e3be044450fd3f9a5d9e11
ms.lasthandoff: 03/13/2017

---
# <a name="how-to-parse-a-string-visual-basic"></a>Comment : analyser une chaîne (Visual Basic)
Cette rubrique montre comment créer une arborescence XML en c#.  
  
## <a name="example"></a>Exemple  
 Vous pouvez analyser une chaîne en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] à l’aide de la `XElement.Parse` méthode. Toutefois, il est plus efficace d'utiliser des littéraux XML, comme illustré dans le code suivant, car leur impact sur les performances n'est pas aussi sévère que l'analyse de code XML à partir d'une chaîne.  
  
 Lorsque vous utilisez des littéraux XML, il vous suffit de copier et coller votre code XML dans votre programme [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  
  
> [!NOTE]
>  L'analyse de texte ou le chargement d'un document XML à partir d'un fichier texte est moins efficace que la construction fonctionnelle. Si vous initialisez une arborescence XML à partir de code, la construction fonctionnelle requiert moins de temps processeur que l’analyse de texte.  
  
```vb  
Dim contacts as XElement = _  
    <Contacts>  
        <Contact>  
            <Name>Patrick Hines</Name>  
            <Phone Type="home">206-555-0144</Phone>  
            <Phone Type="work">425-555-0145</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>10</NetWorth>  
        </Contact>  
        <Contact>  
            <Name>Gretchen Rivas</Name>  
            <Phone Type="mobile">206-555-0163</Phone>  
            <Address>  
            <Street1>123 Main St</Street1>  
            <City>Mercer Island</City>  
            <State>WA</State>  
            <Postal>68042</Postal>  
            </Address>  
            <NetWorth>11</NetWorth>  
        </Contact>  
    </Contacts>  
```  
  
## <a name="see-also"></a>Voir aussi  
 [L’analyse XML (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/parsing-xml.md)

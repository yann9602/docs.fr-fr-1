---
title: "LINQ to XML, différences par rapport à Autres Technologies2 XML | Documents Microsoft"
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
ms.assetid: 72ce3a82-ffc6-488c-98e7-b9b40f3591ec
caps.latest.revision: 3
author: stevehoag
ms.author: shoag
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 0254788fb9efa018e735a57990144c6b176d30d6
ms.lasthandoff: 03/13/2017

---
# <a name="linq-to-xml-vs-other-xml-technologies"></a>LINQ to XML, différences par rapport à d'autres technologies XML
Cette rubrique compare [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] aux technologies XML suivantes : <xref:System.Xml.XmlReader>, XSLT, MSXML et XmlLite.</xref:System.Xml.XmlReader> Ces informations peuvent vous aider à décider de la technologie à utiliser.  
  
 Pour une comparaison de [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] pour le modèle DOM (Document Object), consultez [LINQ to XML vs. DOM (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-vs-dom.md).  
  
## <a name="linq-to-xml-vs-xmlreader"></a>LINQ to XML, différences par rapport à XmlReader  
 <xref:System.Xml.XmlReader>est un analyseur rapide, avant uniquement et non la mise en cache.</xref:System.Xml.XmlReader>  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)]est implémenté sur <xref:System.Xml.XmlReader>, et sont étroitement intégrés.</xref:System.Xml.XmlReader> Toutefois, vous pouvez également utiliser <xref:System.Xml.XmlReader>par lui-même.</xref:System.Xml.XmlReader>  
  
 Par exemple, supposez que vous créez un service Web qui analysera des centaines de documents XML par seconde et que les documents ont la même structure, ce qui signifie que vous n'avez qu'une seule implémentation du code à écrire pour analyser le XML. Dans ce cas, vous souhaiterez probablement utiliser <xref:System.Xml.XmlReader>par lui-même.</xref:System.Xml.XmlReader>  
  
 En revanche, si vous créez un système qui analyse beaucoup de petits documents XML, et chacun d’eux est différent, vous êtes préférable de tirer parti des améliorations de productivité qui [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] fournit.  
  
## <a name="linq-to-xml-vs-xslt"></a>LINQ to XML, différences par rapport à XSLT  
 Les deux [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] et XSLT fournissent des fonctionnalités de transformation de documents XML étendues. XSLT est une approche déclarative basée sur des règles. Les programmeurs XSLT expérimentés écrivent du code XSLT dans un style de programmation fonctionnelle qui met l'accent sur une approche sans état. Les transformations peuvent être écrites à l'aide de fonctions pures implémentées sans effets secondaires. Cette approche fonctionnelle ou basée sur des règles est peu connue de la plupart des développeurs et son apprentissage peut être long et difficile.  
  
 XSLT peut être un système très productif qui génère des applications hautes performances. Par exemple, certaines grandes sociétés basées sur le Web utilisent XSLT afin de générer du code HTML à partir de code XML extrait de différents magasins de données. Le moteur XSLT managé compile XSLT en code CLR et, dans certains scénarios, offre des performances encore meilleures que le moteur XSLT natif.  
  
 Toutefois, XSLT ne tire pas parti des connaissances en C# et Visual Basic que de nombreux développeurs possèdent. Il exige des développeurs qu'ils écrivent du code dans un langage de programmation différent et complexe. L'utilisation de deux systèmes de développement non intégrés tels que C# (ou Visual Basic) et XSLT rend les systèmes logiciels plus difficiles à développer et à gérer.  
  
 Une fois que vous maîtrisez [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] , les expressions de requête [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] les transformations sont une technologie puissante et facile à utiliser. En résumé, vous formez votre document XML à l’aide de la construction fonctionnelle, extrayant des données à partir de différentes sources, en construisant <xref:System.Xml.Linq.XElement>dynamiquement des objets et en assemblant l’ensemble dans une nouvelle arborescence XML.</xref:System.Xml.Linq.XElement> La transformation peut générer un document complètement nouveau. Construction de transformations dans [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] est relativement facile et intuitive, et le code obtenu est lisible. Cela permet de réduire les coûts de développement et de maintenance.  
  
 [!INCLUDE[sqltecxlinq](../../../../csharp/programming-guide/concepts/linq/includes/sqltecxlinq_md.md)] n'a pas pour but de remplacer XSLT. XSLT est toujours l'outil de prédilection pour les transformations XML complexes et centrées sur les documents, en particulier si la structure du document n'est pas bien définie.  
  
 XSLT présente l'avantage d'être une norme World Wide Web Consortium (W3C). Si vous avez l'obligation d'utiliser des technologies qui constituent des normes, il peut être plus judicieux d'utiliser XSLT.  
  
 Le code XSLT étant du code XML, il peut par conséquent être manipulé par programme.  
  
## <a name="linq-to-xml-vs-msxml"></a>LINQ to XML, différences par rapport à MSXML  
 MSXML est une technologie compatible COM pour le traitement du code XML qui est fournie avec Microsoft Windows. MSXML fournit une implémentation native du modèle DOM avec prise en charge de XPath et XSLT. Il contient également l'analyseur sans mise en cache et basé sur les événements SAX2.  
  
 MSXML offre de bonnes performances, est sécurisé par défaut dans la plupart des scénarios et est accessible dans Internet Explorer pour l'exécution de traitement XML du côté client dans les applications de style AJAX. MSXML peut être utilisé à partir de n'importe quel langage de programmation qui prend en charge COM, notamment C++, JavaScript et [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 6.0.  
  
 L'utilisation de MSXML n'est pas recommandée dans le code managé basé sur le Common Language Runtime (CLR).  
  
## <a name="linq-to-xml-vs-xmllite"></a>LINQ to XML, différences par rapport à XmlLite  
 XmlLite est un analyseur de type extraction, avant uniquement et sans mise en cache. Les développeurs utilisent principalement XmlLite avec C++. Il est déconseillé aux développeurs d'utiliser XmlLite avec du code managé.  
  
 Le principal avantage de XmlLite est sa légèreté et sa rapidité d'analyse XML. De plus, il est sécurisé dans la plupart des scénarios. Sa surface de menace est très faible. Si vous devez analyser des documents non approuvés et que vous souhaitez vous protéger contre les attaques de type déni de service ou exposition de données, XmlLite peut constituer un bon choix.  
  
 XmlLite n'est pas intégré à [!INCLUDE[vbteclinqext](../../../../csharp/getting-started/includes/vbteclinqext_md.md)]. Il ne procure pas le programmeur des améliorations de productivité qui constituent la motivation [!INCLUDE[vbteclinq](../../../../csharp/includes/vbteclinq_md.md)].  
  
## <a name="see-also"></a>Voir aussi  
 [Bien démarrer (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/getting-started-linq-to-xml.md)

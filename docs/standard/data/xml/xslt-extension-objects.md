---
title: "Objets d’extension XSLT"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a4ebdbad-087c-4cfe-acc0-17c48142f81a
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 2916f7da6b990cddef9b86559a71b5206351d558
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="xslt-extension-objects"></a>Objets d’extension XSLT
Les objets d’extension permettent d’étendre les fonctionnalités des feuilles de style. Ils sont gérés par la classe <xref:System.Xml.Xsl.XsltArgumentList>.  
  
 L'utilisation d'un objet d'extension plutôt que d'un script intégré présente les avantages suivants :  
  
-   Offre une meilleure encapsulation et réutilisation des classes.  
  
-   Permet aux feuilles de styles d'être plus petites et plus faciles à gérer.  
  
 Des objets d'extension XSLT sont ajoutés à l'objet <xref:System.Xml.Xsl.XsltArgumentList> à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Un nom qualifié et un URI d'espace de noms sont associés à l'objet d'extension à ce stade.  
  
> [!NOTE]
>  Le jeu d'autorisations FullTrust est requis pour appeler la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>. Pour plus d’informations, consultez [Code Access Security](http://msdn.microsoft.com/en-us/23a20143-241d-4fe5-9d9f-3933fd594c03) et [NIB : jeux d’autorisations nommés](http://msdn.microsoft.com/en-us/08250d67-c99d-4ab0-8d2b-b0e12019f6e3).  
  
 Les types de données retournés par les objets d'extension correspondent à l'un des quatre types de données de base XPath : `number`, `string`, `Boolean` et `node set`.  
  
 Les méthodes définies avec le mot clé `params`, qui permet de transmettre un nombre non spécifié de paramètres, ne sont actuellement pas prises en charge par la classe <xref:System.Xml.Xsl.XslCompiledTransform>. Les feuilles de style XSLT qui utilisent une méthode définie avec le mot clé `params` ne fonctionnent pas correctement. Pour plus d’informations, consultez [params](~/docs/csharp/language-reference/keywords/params.md).  
  
### <a name="to-use-an-xslt-extension-object"></a>Pour utiliser un objet d’extension XSLT  
  
1.  Créez un objet <xref:System.Xml.Xsl.XsltArgumentList> et ajoutez l'objet d'extension à l'aide de la méthode <xref:System.Xml.Xsl.XsltArgumentList.AddExtensionObject%2A>.  
  
2.  Appelez l'objet d'extension à partir de la feuille de style.  
  
3.  Transmettez l'objet <xref:System.Xml.Xsl.XsltArgumentList> à la méthode <xref:System.Xml.Xsl.XslCompiledTransform.Transform%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Transformations XSLT](../../../../docs/standard/data/xml/xslt-transformations.md)  
 [Considérations sur la sécurité XSLT](../../../../docs/standard/data/xml/xslt-security-considerations.md)

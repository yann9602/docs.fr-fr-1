---
title: "Comment : spécifier des noms de bases de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b80f0fd2-7f75-45fe-9e12-496f80f183df
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 998a720f4e2cd7c3a63578d1025d0dd7b42a1b92
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-database-names"></a>Comment : spécifier des noms de bases de données
Utilisez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> sur un attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> pour spécifier le nom d'une base de données lorsque la connexion ne fournit pas de nom.  
  
 Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
### <a name="to-specify-the-name-of-the-database"></a>Pour spécifier le nom de la base de données  
  
1.  Ajoutez l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute> à la déclaration de classe de la base de données.  
  
2.  Ajoutez la propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A> à l'attribut <xref:System.Data.Linq.Mapping.DatabaseAttribute>.  
  
3.  Affectez le nom que vous souhaitez spécifier à la valeur de propriété <xref:System.Data.Linq.Mapping.DatabaseAttribute.Name%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Le modèle LINQ to SQL objet](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

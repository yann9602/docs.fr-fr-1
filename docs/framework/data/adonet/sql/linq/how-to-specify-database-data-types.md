---
title: "Comment : spécifier des types de données de base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2228fdad-7e6a-4b1b-b4d1-79d0198b7c28
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: d46c63f5944895311e73524a0ba31a126d768522
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-database-data-types"></a><span data-ttu-id="23b67-102">Comment : spécifier des types de données de base de données</span><span class="sxs-lookup"><span data-stu-id="23b67-102">How to: Specify Database Data Types</span></span>
<span data-ttu-id="23b67-103">Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> propriété sur un <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier le texte exact qui définit la colonne dans une déclaration de table T-SQL.</span><span class="sxs-lookup"><span data-stu-id="23b67-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property on a <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify the exact text that defines the column in a T-SQL table declaration.</span></span>  
  
 <span data-ttu-id="23b67-104">Vous devez spécifier la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> uniquement si vous envisagez d'utiliser <xref:System.Data.Linq.DataContext.CreateDatabase%2A> pour créer une instance de la base de données.</span><span class="sxs-lookup"><span data-stu-id="23b67-104">You must specify the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property only if you plan to use <xref:System.Data.Linq.DataContext.CreateDatabase%2A> to create an instance of the database.</span></span>  
  
 <span data-ttu-id="23b67-105">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span><span class="sxs-lookup"><span data-stu-id="23b67-105">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A>.</span></span>  
  
### <a name="to-specify-text-to-define-a-data-type-in-a-t-sql-table"></a><span data-ttu-id="23b67-106">Pour spécifier du texte afin de définir un type de données dans une table T-SQL</span><span class="sxs-lookup"><span data-stu-id="23b67-106">To specify text to define a data type in a T-SQL table</span></span>  
  
1.  <span data-ttu-id="23b67-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="23b67-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="23b67-108">Affectez la valeur de la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> au texte exact utilisé par T-SQL.</span><span class="sxs-lookup"><span data-stu-id="23b67-108">Set the value of the <xref:System.Data.Linq.Mapping.ColumnAttribute.DbType%2A> property to the exact text that is used by T-SQL.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23b67-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="23b67-109">See Also</span></span>  
 [<span data-ttu-id="23b67-110">Le modèle LINQ to SQL objet</span><span class="sxs-lookup"><span data-stu-id="23b67-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="23b67-111">Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="23b67-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

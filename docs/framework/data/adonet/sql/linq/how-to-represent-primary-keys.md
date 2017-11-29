---
title: "Comment : représenter les clés primaires"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 63c65289-6539-42b2-8493-891c232018fa
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 3510d52f6f6de9ee2e99ebc1e9fc6fa581d58f3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-primary-keys"></a><span data-ttu-id="d70e8-102">Comment : représenter les clés primaires</span><span class="sxs-lookup"><span data-stu-id="d70e8-102">How to: Represent Primary Keys</span></span>
<span data-ttu-id="d70e8-103">Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> propriété sur le <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner une propriété ou un champ pour représenter la clé primaire pour une colonne de base de données.</span><span class="sxs-lookup"><span data-stu-id="d70e8-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a property or field to represent the primary key for a database column.</span></span>  
  
 <span data-ttu-id="d70e8-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span><span class="sxs-lookup"><span data-stu-id="d70e8-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A>.</span></span>  
  
> [!NOTE]
>  [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="d70e8-105"> ne prend pas en charge les colonnes calculées en tant que clés primaires.</span><span class="sxs-lookup"><span data-stu-id="d70e8-105"> does not support computed columns as primary keys.</span></span>  
  
### <a name="to-designate-a-property-or-field-as-a-primary-key"></a><span data-ttu-id="d70e8-106">Pour désigner une propriété ou un champ comme clé primaire</span><span class="sxs-lookup"><span data-stu-id="d70e8-106">To designate a property or field as a primary key</span></span>  
  
1.  <span data-ttu-id="d70e8-107">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="d70e8-107">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsPrimaryKey%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="d70e8-108">Affectez la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="d70e8-108">Specify the value as `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d70e8-109">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="d70e8-109">See Also</span></span>  
 [<span data-ttu-id="d70e8-110">Le modèle LINQ to SQL objet</span><span class="sxs-lookup"><span data-stu-id="d70e8-110">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="d70e8-111">Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="d70e8-111">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

---
title: "Comment : représenter des colonnes en tant que colonnes autorisant les valeurs Null"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ebb71a37-1f4c-4fa7-b2d2-d903f13c4af1
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: efa6f9d453940151dfe01d27827760521359ab67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-allowing-null-values"></a><span data-ttu-id="6874a-102">Comment : représenter des colonnes en tant que colonnes autorisant les valeurs Null</span><span class="sxs-lookup"><span data-stu-id="6874a-102">How to: Represent Columns as Allowing Null Values</span></span>
<span data-ttu-id="6874a-103">Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> propriété sur le <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour spécifier que la colonne de base de données associée peut contenir des valeurs null.</span><span class="sxs-lookup"><span data-stu-id="6874a-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to specify that the associated database column can hold null values.</span></span>  
  
 <span data-ttu-id="6874a-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span><span class="sxs-lookup"><span data-stu-id="6874a-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A>.</span></span>  
  
### <a name="to-designate-a-column-as-allowing-null-values"></a><span data-ttu-id="6874a-105">Pour désigner une colonne comme autorisant des valeurs null</span><span class="sxs-lookup"><span data-stu-id="6874a-105">To designate a column as allowing null values</span></span>  
  
1.  <span data-ttu-id="6874a-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="6874a-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="6874a-107">Affectez la valeur <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> à la propriété `true`.</span><span class="sxs-lookup"><span data-stu-id="6874a-107">Set the <xref:System.Data.Linq.Mapping.ColumnAttribute.CanBeNull%2A> property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6874a-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="6874a-108">See Also</span></span>  
 [<span data-ttu-id="6874a-109">Le modèle LINQ to SQL objet</span><span class="sxs-lookup"><span data-stu-id="6874a-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="6874a-110">Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="6874a-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

---
title: "Comment : représenter des colonnes en tant que colonnes générées par une base de données"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6524b8a6-e5d2-4a3b-8e08-beafc4a84fd2
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: a0b36e7035b885985e70203146957cdfca92148b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-represent-columns-as-database-generated"></a><span data-ttu-id="101f0-102">Comment : représenter des colonnes en tant que colonnes générées par une base de données</span><span class="sxs-lookup"><span data-stu-id="101f0-102">How to: Represent Columns as Database-Generated</span></span>
<span data-ttu-id="101f0-103">Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> propriété sur le <xref:System.Data.Linq.Mapping.ColumnAttribute> attribut pour désigner un champ ou une propriété comme représentant d’une colonne de base de données générée.</span><span class="sxs-lookup"><span data-stu-id="101f0-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property on the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute to designate a field or property as representing a database-generated column.</span></span>  
  
 <span data-ttu-id="101f0-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span><span class="sxs-lookup"><span data-stu-id="101f0-104">For code examples, see <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A>.</span></span>  
  
### <a name="to-designate-a-field-or-property-as-representing-a-database-generated-column"></a><span data-ttu-id="101f0-105">Pour désigner un champ ou une propriété comme représentant d'une colonne générée par une base de données</span><span class="sxs-lookup"><span data-stu-id="101f0-105">To designate a field or property as representing a database-generated column</span></span>  
  
1.  <span data-ttu-id="101f0-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="101f0-106">Add the <xref:System.Data.Linq.Mapping.ColumnAttribute.IsDbGenerated%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="101f0-107">Affectez la valeur `true`.</span><span class="sxs-lookup"><span data-stu-id="101f0-107">Set the property value to `true`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="101f0-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="101f0-108">See Also</span></span>  
 [<span data-ttu-id="101f0-109">Le modèle LINQ to SQL objet</span><span class="sxs-lookup"><span data-stu-id="101f0-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="101f0-110">Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="101f0-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

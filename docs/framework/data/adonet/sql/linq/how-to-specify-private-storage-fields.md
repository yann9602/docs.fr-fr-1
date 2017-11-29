---
title: "Comment : spécifier des champs de stockage privés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5a40e816-cc6e-43a0-b32a-9caaa0ab6912
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 1095189eaefa8fe34dd554a982110754bb3bd135
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-specify-private-storage-fields"></a><span data-ttu-id="cb853-102">Comment : spécifier des champs de stockage privés</span><span class="sxs-lookup"><span data-stu-id="cb853-102">How to: Specify Private Storage Fields</span></span>
<span data-ttu-id="cb853-103">Utilisez le [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> propriété sur le <xref:System.Data.Linq.Mapping.DataAttribute> attribut pour désigner le nom d’un champ de stockage sous-jacent.</span><span class="sxs-lookup"><span data-stu-id="cb853-103">Use the [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property on the <xref:System.Data.Linq.Mapping.DataAttribute> attribute to designate the name of an underlying storage field.</span></span>  
  
 <span data-ttu-id="cb853-104">Pour obtenir des exemples de code, consultez <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb853-104">For code examples, see <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span></span>  
  
### <a name="to-specify-the-name-of-an-underlying-storage-field"></a><span data-ttu-id="cb853-105">Pour spécifier le nom d'un champ de stockage sous-jacent</span><span class="sxs-lookup"><span data-stu-id="cb853-105">To specify the name of an underlying storage field</span></span>  
  
1.  <span data-ttu-id="cb853-106">Ajoutez la propriété <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> à l'attribut <xref:System.Data.Linq.Mapping.ColumnAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cb853-106">Add the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property to the <xref:System.Data.Linq.Mapping.ColumnAttribute> attribute.</span></span>  
  
2.  <span data-ttu-id="cb853-107">Assignez le nom du champ comme valeur de la propriété <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A>.</span><span class="sxs-lookup"><span data-stu-id="cb853-107">Assign the name of the field as the value of the <xref:System.Data.Linq.Mapping.DataAttribute.Storage%2A> property.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cb853-108">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="cb853-108">See Also</span></span>  
 [<span data-ttu-id="cb853-109">Le modèle LINQ to SQL objet</span><span class="sxs-lookup"><span data-stu-id="cb853-109">The LINQ to SQL Object Model</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/the-linq-to-sql-object-model.md)  
 [<span data-ttu-id="cb853-110">Comment : personnaliser des Classes d’entité à l’aide de l’éditeur de Code</span><span class="sxs-lookup"><span data-stu-id="cb853-110">How to: Customize Entity Classes by Using the Code Editor</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-customize-entity-classes-by-using-the-code-editor.md)

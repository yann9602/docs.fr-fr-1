---
title: ". (Accès aux membres) (Entity SQL)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4733e3b2-3efa-4b96-b591-ac31350e96ad
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: c90c908e567ac05f344292411978ff0c80919a65
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/17/2018
---
# <a name="-member-access-entity-sql"></a><span data-ttu-id="7dd75-103">.</span><span class="sxs-lookup"><span data-stu-id="7dd75-103">.</span></span> <span data-ttu-id="7dd75-104">(Accès aux membres) (Entity SQL)</span><span class="sxs-lookup"><span data-stu-id="7dd75-104">(Member Access) (Entity SQL)</span></span>
<span data-ttu-id="7dd75-105">L’opérateur point (.) est le [!INCLUDE[esql](../../../../../../includes/esql-md.md)] opérateur d’accès au membre.</span><span class="sxs-lookup"><span data-stu-id="7dd75-105">The dot operator (.) is the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] member access operator.</span></span> <span data-ttu-id="7dd75-106">L'opérateur d'accès aux membres permet de produire la valeur d'une propriété ou d'un champ d'une instance de type de modèle conceptuel structurel.</span><span class="sxs-lookup"><span data-stu-id="7dd75-106">You use the member access operator to yield the value of a property or field of an instance of structural conceptual model type.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7dd75-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7dd75-107">Syntax</span></span>  
  
```  
expression.identifier  
```  
  
## <a name="arguments"></a><span data-ttu-id="7dd75-108">Arguments</span><span class="sxs-lookup"><span data-stu-id="7dd75-108">Arguments</span></span>  
 `expression`  
 <span data-ttu-id="7dd75-109">Instance d'un type de modèle conceptuel structurel.</span><span class="sxs-lookup"><span data-stu-id="7dd75-109">An instance of a structural conceptual model type.</span></span>  
  
 `identifier`  
 <span data-ttu-id="7dd75-110">Propriété ou champ appartenant à une instance d'objet.</span><span class="sxs-lookup"><span data-stu-id="7dd75-110">A property or field that belongs to an object instance.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7dd75-111">Notes</span><span class="sxs-lookup"><span data-stu-id="7dd75-111">Remarks</span></span>  
 <span data-ttu-id="7dd75-112">L'opérateur point (.) peut être utilisé pour extraire les champs d'un enregistrement, de la même manière que l'on extrait les propriétés d'un type complexe ou d'un type d'entité.</span><span class="sxs-lookup"><span data-stu-id="7dd75-112">The dot (.) operator may be used to extract fields from a record, similar to extracting properties of a complex or entity type.</span></span> <span data-ttu-id="7dd75-113">Par exemple, si n de type Nom est membre du type Personne et que p est une instance du type Personne, alors p.n est une expression d'accès aux membres valide qui produit une valeur de type Nom.</span><span class="sxs-lookup"><span data-stu-id="7dd75-113">For example, if n of type Name is a member of type Person, and p is an instance of type Person, then p.n is a legal member access expression that yields a value of type Name.</span></span>  
  
 `select p.Name.FirstName from LOB.Person as p`  
  
## <a name="see-also"></a><span data-ttu-id="7dd75-114">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="7dd75-114">See Also</span></span>  
 [<span data-ttu-id="7dd75-115">Référence Entity SQL</span><span class="sxs-lookup"><span data-stu-id="7dd75-115">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)

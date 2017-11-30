---
title: "Opérateur GetType (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.GetType
helpviewer_keywords:
- GetType operator [Visual Basic]
- GetType keyword [Visual Basic]
ms.assetid: 4f733297-2503-4607-850c-15eba65fff90
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 38a984dce44133936f7f163e6afb20f0f336377c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2017
---
# <a name="gettype-operator-visual-basic"></a><span data-ttu-id="35f68-102">Opérateur GetType (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="35f68-102">GetType Operator (Visual Basic)</span></span>
<span data-ttu-id="35f68-103">Retourne un <xref:System.Type> objet pour le type spécifié.</span><span class="sxs-lookup"><span data-stu-id="35f68-103">Returns a <xref:System.Type> object for the specified type.</span></span> <span data-ttu-id="35f68-104">Le <xref:System.Type> objet fournit des informations sur le type telles que ses propriétés, méthodes et événements.</span><span class="sxs-lookup"><span data-stu-id="35f68-104">The <xref:System.Type> object provides information about the type such as its properties, methods, and events.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="35f68-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="35f68-105">Syntax</span></span>  
  
```  
GetType(typename)  
```  
  
#### <a name="parameters"></a><span data-ttu-id="35f68-106">Paramètres</span><span class="sxs-lookup"><span data-stu-id="35f68-106">Parameters</span></span>  
  
|<span data-ttu-id="35f68-107">Paramètre</span><span class="sxs-lookup"><span data-stu-id="35f68-107">Parameter</span></span>|<span data-ttu-id="35f68-108">Description</span><span class="sxs-lookup"><span data-stu-id="35f68-108">Description</span></span>|  
|---|---|  
|`typename`|<span data-ttu-id="35f68-109">Le nom du type pour lequel vous souhaitez des informations.</span><span class="sxs-lookup"><span data-stu-id="35f68-109">The name of the type for which you desire information.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="35f68-110">Remarques</span><span class="sxs-lookup"><span data-stu-id="35f68-110">Remarks</span></span>  
 <span data-ttu-id="35f68-111">Le `GetType` opérateur retourne le <xref:System.Type> objet spécifié `typename`.</span><span class="sxs-lookup"><span data-stu-id="35f68-111">The `GetType` operator returns the <xref:System.Type> object for the specified `typename`.</span></span> <span data-ttu-id="35f68-112">Vous pouvez passer le nom de tout type défini dans `typename`.</span><span class="sxs-lookup"><span data-stu-id="35f68-112">You can pass the name of any defined type in `typename`.</span></span> <span data-ttu-id="35f68-113">Ce dernier est détaillé ci-après :</span><span class="sxs-lookup"><span data-stu-id="35f68-113">This includes the following:</span></span>  
  
-   <span data-ttu-id="35f68-114">Type de données Visual Basic, tel que `Boolean` ou `Date`.</span><span class="sxs-lookup"><span data-stu-id="35f68-114">Any Visual Basic data type, such as `Boolean` or `Date`.</span></span>  
  
-   <span data-ttu-id="35f68-115">Toute classe .NET Framework, structure, module ou interface, tel que <xref:System.ArgumentException?displayProperty=nameWithType> ou <xref:System.Double?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35f68-115">Any .NET Framework class, structure, module, or interface, such as <xref:System.ArgumentException?displayProperty=nameWithType> or <xref:System.Double?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="35f68-116">Toute classe, structure, module ou interface définie par votre application.</span><span class="sxs-lookup"><span data-stu-id="35f68-116">Any class, structure, module, or interface defined by your application.</span></span>  
  
-   <span data-ttu-id="35f68-117">Tout tableau défini par votre application.</span><span class="sxs-lookup"><span data-stu-id="35f68-117">Any array defined by your application.</span></span>  
  
-   <span data-ttu-id="35f68-118">Tout délégué défini par votre application.</span><span class="sxs-lookup"><span data-stu-id="35f68-118">Any delegate defined by your application.</span></span>  
  
-   <span data-ttu-id="35f68-119">Toute énumération définie par votre application, le .NET Framework ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="35f68-119">Any enumeration defined by Visual Basic, the .NET Framework, or your application.</span></span>  
  
 <span data-ttu-id="35f68-120">Si vous souhaitez obtenir l’objet de type d’une variable objet, utilisez le <xref:System.Type.GetType%2A?displayProperty=nameWithType> (méthode).</span><span class="sxs-lookup"><span data-stu-id="35f68-120">If you want to get the type object of an object variable, use the <xref:System.Type.GetType%2A?displayProperty=nameWithType> method.</span></span>  
  
 <span data-ttu-id="35f68-121">Le `GetType` opérateur peut être utile dans les circonstances suivantes :</span><span class="sxs-lookup"><span data-stu-id="35f68-121">The `GetType` operator can be useful in the following circumstances:</span></span>  
  
-   <span data-ttu-id="35f68-122">Vous devez accéder à des métadonnées pour un type au moment de l’exécution.</span><span class="sxs-lookup"><span data-stu-id="35f68-122">You must access the metadata for a type at run time.</span></span> <span data-ttu-id="35f68-123">Le <xref:System.Type> objet qui fournit des métadonnées telles que les membres de type et des informations sur le déploiement.</span><span class="sxs-lookup"><span data-stu-id="35f68-123">The <xref:System.Type> object supplies metadata such as type members and deployment information.</span></span> <span data-ttu-id="35f68-124">Vous devez, par exemple, réfléchir à un assembly.</span><span class="sxs-lookup"><span data-stu-id="35f68-124">You need this, for example, to reflect over an assembly.</span></span> <span data-ttu-id="35f68-125">Pour plus d'informations, consultez <xref:System.Reflection?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="35f68-125">For more information, see <xref:System.Reflection?displayProperty=nameWithType>.</span></span>  
  
-   <span data-ttu-id="35f68-126">Vous souhaitez comparer deux références d’objet pour voir s’ils font référence à des instances du même type.</span><span class="sxs-lookup"><span data-stu-id="35f68-126">You want to compare two object references to see if they refer to instances of the same type.</span></span> <span data-ttu-id="35f68-127">Dans le cas, `GetType` retourne des références au même <xref:System.Type> objet.</span><span class="sxs-lookup"><span data-stu-id="35f68-127">If they do, `GetType` returns references to the same <xref:System.Type> object.</span></span>  
  
## <a name="example"></a><span data-ttu-id="35f68-128">Exemple</span><span class="sxs-lookup"><span data-stu-id="35f68-128">Example</span></span>  
 <span data-ttu-id="35f68-129">Les exemples suivants illustrent la `GetType` opérateur en cours d’utilisation.</span><span class="sxs-lookup"><span data-stu-id="35f68-129">The following examples show the `GetType` operator in use.</span></span>  
  
 [!code-vb[VbVbalrOperators#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/gettype-operator_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="35f68-130">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="35f68-130">See Also</span></span>  
 [<span data-ttu-id="35f68-131">Priorité des opérateurs en Visual Basic</span><span class="sxs-lookup"><span data-stu-id="35f68-131">Operator Precedence in Visual Basic</span></span>](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [<span data-ttu-id="35f68-132">Opérateurs répertoriés par fonctionnalité</span><span class="sxs-lookup"><span data-stu-id="35f68-132">Operators Listed by Functionality</span></span>](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [<span data-ttu-id="35f68-133">Opérateurs et expressions</span><span class="sxs-lookup"><span data-stu-id="35f68-133">Operators and Expressions</span></span>](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)

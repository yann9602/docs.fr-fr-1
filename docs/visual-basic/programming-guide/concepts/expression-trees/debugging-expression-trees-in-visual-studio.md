---
title: "Débogage d’arborescences d’Expression dans Visual Studio (Visual Basic) | Documents Microsoft"
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
ms.assetid: 492cc28f-b7a2-4c47-b582-b3c437b8a5d5
caps.latest.revision: 4
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: 9f5b8ebb69c9206ff90b05e748c64d29d82f7a16
ms.openlocfilehash: 84de749afad6abb748d0622561f8ee7cd399ed54
ms.contentlocale: fr-fr
ms.lasthandoff: 04/12/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a><span data-ttu-id="ab2f6-102">Débogage d’arborescences d’Expression dans Visual Studio (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ab2f6-102">Debugging Expression Trees in Visual Studio (Visual Basic)</span></span>
<span data-ttu-id="ab2f6-103">Vous pouvez analyser la structure et le contenu des arborescences d’expressions lorsque vous déboguez vos applications.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-103">You can analyze the structure and content of expression trees when you debug your applications.</span></span> <span data-ttu-id="ab2f6-104">Pour obtenir un aperçu rapide de l’arborescence d’expression, vous pouvez utiliser le `DebugView` propriété, qui est disponible uniquement en mode débogage.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-104">To get a quick overview of the expression tree structure, you can use the `DebugView` property, which is available only in debug mode.</span></span> <span data-ttu-id="ab2f6-105">Pour plus d’informations sur le débogage, consultez [débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span><span class="sxs-lookup"><span data-stu-id="ab2f6-105">For more information about debugging, see [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).</span></span>  
  
 <span data-ttu-id="ab2f6-106">Afin de mieux représenter le contenu des arborescences d’expression, le `DebugView` propriété utilise des visualiseurs Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-106">To better represent the content of expression trees, the `DebugView` property uses Visual Studio visualizers.</span></span> <span data-ttu-id="ab2f6-107">Pour plus d’informations, consultez [créer des visualiseurs personnalisés](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span><span class="sxs-lookup"><span data-stu-id="ab2f6-107">For more information, see [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).</span></span>  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a><span data-ttu-id="ab2f6-108">Pour ouvrir un visualiseur pour une arborescence d’expression</span><span class="sxs-lookup"><span data-stu-id="ab2f6-108">To open a visualizer for an expression tree</span></span>  
  
1.  <span data-ttu-id="ab2f6-109">Cliquez sur l’icône de loupe qui apparaît en regard du `DebugView` propriété d’une arborescence d’expression dans **DataTips**, un **espion** fenêtre, le **automatique** fenêtre, ou la **variables locales** fenêtre.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-109">Click the magnifying glass icon that appears next to the `DebugView` property of an expression tree in **DataTips**, a **Watch** window, the **Autos** window, or the **Locals** window.</span></span>  
  
     <span data-ttu-id="ab2f6-110">Une liste de visualiseurs s'affiche.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-110">A list of visualizers is displayed.</span></span>  
  
2.  <span data-ttu-id="ab2f6-111">Cliquez sur le visualiseur à utiliser.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-111">Click the visualizer you want to use.</span></span>  
  
 <span data-ttu-id="ab2f6-112">Chaque type d’expression s’affiche dans le visualiseur, comme décrit dans les sections suivantes.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-112">Each expression type is displayed in the visualizer as described in the following sections.</span></span>  
  
## <a name="parameterexpressions"></a><span data-ttu-id="ab2f6-113">ParameterExpressions</span><span class="sxs-lookup"><span data-stu-id="ab2f6-113">ParameterExpressions</span></span>  
 <span data-ttu-id="ab2f6-114"><xref:System.Linq.Expressions.ParameterExpression>les noms de variables sont affichés avec le symbole « $» au début.</xref:System.Linq.Expressions.ParameterExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-114"><xref:System.Linq.Expressions.ParameterExpression> variable names are displayed with a "$" symbol at the beginning.</span></span>  
  
 <span data-ttu-id="ab2f6-115">Si un paramètre n’a pas un nom, il est attribué un nom généré automatiquement, tel que `$var1` ou `$var2`.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-115">If a parameter does not have a name, it is assigned an automatically generated name, such as `$var1` or `$var2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-116">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-116">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     <span data-ttu-id="ab2f6-117">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-117">`DebugView` property</span></span>  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     <span data-ttu-id="ab2f6-118">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-118">`DebugView` property</span></span>  
  
     `$var1`  
  
## <a name="constantexpressions"></a><span data-ttu-id="ab2f6-119">ConstantExpressions</span><span class="sxs-lookup"><span data-stu-id="ab2f6-119">ConstantExpressions</span></span>  
 <span data-ttu-id="ab2f6-120">Pour <xref:System.Linq.Expressions.ConstantExpression>les objets qui représentent des entiers, chaînes, et `null`, la valeur de la constante est affichée.</xref:System.Linq.Expressions.ConstantExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-120">For <xref:System.Linq.Expressions.ConstantExpression> objects that represent integer values, strings, and `null`, the value of the constant is displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-121">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-121">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="ab2f6-122">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-122">`DebugView` property</span></span>  
  
     <span data-ttu-id="ab2f6-123">10</span><span class="sxs-lookup"><span data-stu-id="ab2f6-123">10</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     <span data-ttu-id="ab2f6-124">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-124">`DebugView` property</span></span>  
  
     <span data-ttu-id="ab2f6-125">D&10;</span><span class="sxs-lookup"><span data-stu-id="ab2f6-125">10D</span></span>  
  
## <a name="blockexpression"></a><span data-ttu-id="ab2f6-126">BlockExpression</span><span class="sxs-lookup"><span data-stu-id="ab2f6-126">BlockExpression</span></span>  
 <span data-ttu-id="ab2f6-127">Si le type d’un <xref:System.Linq.Expressions.BlockExpression>objet est différent du type de la dernière expression dans le bloc, le type est affiché dans le `DebugInfo` propriété crochets pointus (\< et >).</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-127">If the type of a <xref:System.Linq.Expressions.BlockExpression> object differs from the type of the last expression in the block, the type is displayed in the `DebugInfo` property in angle brackets (\< and >).</span></span> <span data-ttu-id="ab2f6-128">Dans le cas contraire, le type de la <xref:System.Linq.Expressions.BlockExpression>objet n’est pas affiché.</xref:System.Linq.Expressions.BlockExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-128">Otherwise, the type of the <xref:System.Linq.Expressions.BlockExpression> object is not displayed.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-129">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-129">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="ab2f6-130">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-130">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     <span data-ttu-id="ab2f6-131">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-131">`DebugView` property</span></span>  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a><span data-ttu-id="ab2f6-132">LambdaExpression.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-132">LambdaExpression</span></span>  
 <span data-ttu-id="ab2f6-133"><xref:System.Linq.Expressions.LambdaExpression>les objets sont affichés avec leurs types délégués.</xref:System.Linq.Expressions.LambdaExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-133"><xref:System.Linq.Expressions.LambdaExpression> objects are displayed together with their delegate types.</span></span>  
  
 <span data-ttu-id="ab2f6-134">Si une expression lambda n’a pas un nom, il est attribué un nom généré automatiquement, tel que `#Lambda1` ou `#Lambda2`.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-134">If a lambda expression does not have a name, it is assigned an automatically generated name, such as `#Lambda1` or `#Lambda2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-135">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-135">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     <span data-ttu-id="ab2f6-136">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-136">`DebugView` property</span></span>  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     <span data-ttu-id="ab2f6-137">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-137">`DebugView` property</span></span>  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a><span data-ttu-id="ab2f6-138">LabelExpression</span><span class="sxs-lookup"><span data-stu-id="ab2f6-138">LabelExpression</span></span>  
 <span data-ttu-id="ab2f6-139">Si vous spécifiez une valeur par défaut pour le <xref:System.Linq.Expressions.LabelExpression>de l’objet, cette valeur est affichée avant le <xref:System.Linq.Expressions.LabelTarget>objet.</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression></span><span class="sxs-lookup"><span data-stu-id="ab2f6-139">If you specify a default value for the <xref:System.Linq.Expressions.LabelExpression> object, this value is displayed before the <xref:System.Linq.Expressions.LabelTarget> object.</span></span>  
  
 <span data-ttu-id="ab2f6-140">Le `.Label` jeton indique le début de l’étiquette.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-140">The `.Label` token indicates the start of the label.</span></span> <span data-ttu-id="ab2f6-141">Le `.LabelTarget` jeton indique la destination de la cible à atteindre.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-141">The `.LabelTarget` token indicates the destination of the target to jump to.</span></span>  
  
 <span data-ttu-id="ab2f6-142">Si une étiquette est un nom, il est attribué un nom généré automatiquement, tel que `#Label1` ou `#Label2`.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-142">If a label does not have a name, it is assigned an automatically generated name, such as `#Label1` or `#Label2`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-143">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-143">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     <span data-ttu-id="ab2f6-144">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-144">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto SampleLabel { 0 };`  
  
     `.Label`  
  
     `-1`  
  
     `.LabelTarget SampleLabel:`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label()  
    Dim block As BlockExpression = Expression.Block(  
    Expression.Goto(target), Expression.Label(target))  
    ```  
  
     <span data-ttu-id="ab2f6-145">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-145">`DebugView` property</span></span>  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a><span data-ttu-id="ab2f6-146">Opérateurs checked</span><span class="sxs-lookup"><span data-stu-id="ab2f6-146">Checked Operators</span></span>  
 <span data-ttu-id="ab2f6-147">Opérateurs checked sont affichés avec le symbole « # » devant l’opérateur.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-147">Checked operators are displayed with the "#" symbol in front of the operator.</span></span> <span data-ttu-id="ab2f6-148">Par exemple, l’opérateur d’addition checked est affiché en tant que `#+`.</span><span class="sxs-lookup"><span data-stu-id="ab2f6-148">For example, the checked addition operator is displayed as `#+`.</span></span>  
  
### <a name="examples"></a><span data-ttu-id="ab2f6-149">Exemples</span><span class="sxs-lookup"><span data-stu-id="ab2f6-149">Examples</span></span>  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     <span data-ttu-id="ab2f6-150">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-150">`DebugView` property</span></span>  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     <span data-ttu-id="ab2f6-151">Propriété `DebugView`</span><span class="sxs-lookup"><span data-stu-id="ab2f6-151">`DebugView` property</span></span>  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a><span data-ttu-id="ab2f6-152">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ab2f6-152">See Also</span></span>  
 <span data-ttu-id="ab2f6-153">[Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span><span class="sxs-lookup"><span data-stu-id="ab2f6-153">[Expression Trees (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md) </span></span>  
<span data-ttu-id="ab2f6-154"> [Débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span><span class="sxs-lookup"><span data-stu-id="ab2f6-154"> [Debugging in Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio) </span></span>  
<span data-ttu-id="ab2f6-155"> [Créer des visualiseurs personnalisés](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span><span class="sxs-lookup"><span data-stu-id="ab2f6-155"> [Create Custom Visualizers](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)</span></span>

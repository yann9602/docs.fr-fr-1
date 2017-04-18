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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: efbd8c19947c45b3ba15ce7b574000d56526ef45
ms.lasthandoff: 03/13/2017

---
# <a name="debugging-expression-trees-in-visual-studio-visual-basic"></a>Débogage d’arborescences d’Expression dans Visual Studio (Visual Basic)
Vous pouvez analyser la structure et le contenu des arborescences d’expressions lorsque vous déboguez vos applications. Pour obtenir un aperçu rapide de l’arborescence d’expression, vous pouvez utiliser le `DebugView` propriété, qui est disponible uniquement en mode débogage. Pour plus d’informations sur le débogage, consultez [débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio).  
  
 Afin de mieux représenter le contenu des arborescences d’expression, le `DebugView` propriété utilise des visualiseurs Visual Studio. Pour plus d’informations, consultez [créer des visualiseurs personnalisés](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data).  
  
### <a name="to-open-a-visualizer-for-an-expression-tree"></a>Pour ouvrir un visualiseur pour une arborescence d’expression  
  
1.  Cliquez sur l’icône de loupe qui apparaît en regard du `DebugView` propriété d’une arborescence d’expression dans **DataTips**, un **espion** fenêtre, le **automatique** fenêtre, ou la **variables locales** fenêtre.  
  
     Une liste de visualiseurs s'affiche.  
  
2.  Cliquez sur le visualiseur à utiliser.  
  
 Chaque type d’expression s’affiche dans le visualiseur, comme décrit dans les sections suivantes.  
  
## <a name="parameterexpressions"></a>ParameterExpressions  
 <xref:System.Linq.Expressions.ParameterExpression>les noms de variables sont affichés avec le symbole « $» au début.</xref:System.Linq.Expressions.ParameterExpression>  
  
 Si un paramètre n’a pas un nom, il est attribué un nom généré automatiquement, tel que `$var1` ou `$var2`.  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer), "num")  
    ```  
  
     Propriété `DebugView`  
  
     `$num`  
  
-   `Expression`  
  
    ```vb  
    Dim numParam As ParameterExpression =   
    Expression.Parameter(GetType(Integer))  
    ```  
  
     Propriété `DebugView`  
  
     `$var1`  
  
## <a name="constantexpressions"></a>ConstantExpressions  
 Pour <xref:System.Linq.Expressions.ConstantExpression>les objets qui représentent des entiers, chaînes, et `null`, la valeur de la constante est affichée.</xref:System.Linq.Expressions.ConstantExpression>  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim num as Integer= 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     Propriété `DebugView`  
  
     10  
  
-   `Expression`  
  
    ```vb  
    Dim num As Double = 10  
    Dim expr As ConstantExpression = Expression.Constant(num)  
    ```  
  
     Propriété `DebugView`  
  
     D&10;  
  
## <a name="blockexpression"></a>BlockExpression  
 Si le type d’un <xref:System.Linq.Expressions.BlockExpression>objet est différent du type de la dernière expression dans le bloc, le type est affiché dans le `DebugInfo` propriété crochets pointus (\< et >).</xref:System.Linq.Expressions.BlockExpression> Dans le cas contraire, le type de la <xref:System.Linq.Expressions.BlockExpression>objet n’est pas affiché.</xref:System.Linq.Expressions.BlockExpression>  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression = Expression.Block(Expression.Constant("test"))  
    ```  
  
     Propriété `DebugView`  
  
     `.Block() {`  
  
     `"test"`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim block As BlockExpression =   
    Expression.Block(GetType(Object), Expression.Constant("test"))  
    ```  
  
     Propriété `DebugView`  
  
     `.Block<System.Object>() {`  
  
     `"test"`  
  
     `}`  
  
## <a name="lambdaexpression"></a>LambdaExpression.  
 <xref:System.Linq.Expressions.LambdaExpression>les objets sont affichés avec leurs types délégués.</xref:System.Linq.Expressions.LambdaExpression>  
  
 Si une expression lambda n’a pas un nom, il est attribué un nom généré automatiquement, tel que `#Lambda1` ou `#Lambda2`.  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1))  
    ```  
  
     Propriété `DebugView`  
  
     `.Lambda #Lambda1<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
-   `Expression`  
  
    ```vb  
    Dim lambda As LambdaExpression =   
    Expression.Lambda(Of Func(Of Integer))(Expression.Constant(1), "SampleLamda", Nothing)  
    ```  
  
     Propriété `DebugView`  
  
     `.Lambda SampleLambda<System.Func'1[System.Int32]>() {`  
  
     `1`  
  
     `}`  
  
## <a name="labelexpression"></a>LabelExpression  
 Si vous spécifiez une valeur par défaut pour le <xref:System.Linq.Expressions.LabelExpression>de l’objet, cette valeur est affichée avant le <xref:System.Linq.Expressions.LabelTarget>objet.</xref:System.Linq.Expressions.LabelTarget> </xref:System.Linq.Expressions.LabelExpression>  
  
 Le `.Label` jeton indique le début de l’étiquette. Le `.LabelTarget` jeton indique la destination de la cible à atteindre.  
  
 Si une étiquette est un nom, il est attribué un nom généré automatiquement, tel que `#Label1` ou `#Label2`.  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim target As LabelTarget = Expression.Label(GetType(Integer), "SampleLabel")  
    Dim label1 As BlockExpression = Expression.Block(  
    Expression.Goto(target, Expression.Constant(0)),  
    Expression.Label(target, Expression.Constant(-1)))  
    ```  
  
     Propriété `DebugView`  
  
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
  
     Propriété `DebugView`  
  
     `.Block() {`  
  
     `.Goto #Label1 { };`  
  
     `.Label`  
  
     `.LabelTarget #Label1:`  
  
     `}`  
  
## <a name="checked-operators"></a>Opérateurs checked  
 Opérateurs checked sont affichés avec le symbole « # » devant l’opérateur. Par exemple, l’opérateur d’addition checked est affiché en tant que `#+`.  
  
### <a name="examples"></a>Exemples  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.AddChecked(  
    Expression.Constant(1), Expression.Constant(2))  
    ```  
  
     Propriété `DebugView`  
  
     `1 #+ 2`  
  
-   `Expression`  
  
    ```vb  
    Dim expr As Expression = Expression.ConvertChecked(  
    Expression.Constant(10.0), GetType(Integer))  
    ```  
  
     Propriété `DebugView`  
  
     `#(System.Int32)10D`  
  
## <a name="see-also"></a>Voir aussi  
 [Arborescences d’expression (Visual Basic)](../../../../visual-basic/programming-guide/concepts/expression-trees/index.md)   
 [Débogage dans Visual Studio](https://docs.microsoft.com/visualstudio/debugger/debugging-in-visual-studio)   
 [Créer des visualiseurs personnalisés](https://docs.microsoft.com/visualstudio/debugger/create-custom-visualizers-of-data)

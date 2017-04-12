---
title: "Procédure pas à pas : Implémentation de l’héritage avec les objets COM (Visual Basic) | Documents Microsoft"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- inheritance, COM reusability
- base classes, COM reusability
- inheritance, walkthroughs
- derived classes, COM reusability
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: fa7753847619f14600c924cba01e55651c4f17c2
ms.lasthandoff: 03/13/2017

---
# <a name="walkthrough-implementing-inheritance-with-com-objects-visual-basic"></a>Procédure pas à pas : implémentation de l'héritage avec les objets COM (Visual Basic)
Vous pouvez dériver des classes Visual Basic à partir de `Public` classes dans les objets COM, même ceux créés dans les versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]. Les propriétés et méthodes des classes héritées d’objets COM peuvent être substituées ou surchargées comme les propriétés et méthodes de toute autre classe de base peuvent être substituées ou surchargés. Héritage à partir d’objets COM est utile lorsque vous disposez d’une bibliothèque de classe existante que vous ne souhaitez pas recompiler.  
  
 La procédure suivante montre comment utiliser Visual Basic 6.0 pour créer un objet COM contenant une classe, puis l’utiliser comme classe de base.  
  
[!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### <a name="to-build-the-com-object-that-is-used-in-this-walkthrough"></a>Pour générer l’objet COM qui est utilisé dans cette procédure pas à pas  
  
1.  Dans Visual Basic 6.0, ouvrez un nouveau projet de DLL ActiveX. Un projet nommé `Project1` est créé. Il a une classe nommée `Class1`.  
  
2.  Dans le **Explorateur de projets**, avec le bouton droit **Project1**, puis cliquez sur **Project1 propriétés**. Le **propriétés du projet** boîte de dialogue s’affiche.  
  
3.  Sur le **général** onglet de la **propriétés du projet** boîte de dialogue, remplacez le nom du projet en tapant `ComObject1` dans les **le nom du projet** champ.  
  
4.  Dans le **Explorateur de projets**, avec le bouton droit `Class1`, puis cliquez sur **propriétés**. Le **propriétés** fenêtre de la classe s’affiche.  
  
5.  Modifier la `Name` propriété `MathFunctions`.  
  
6.  Dans le **Explorateur de projets**, avec le bouton droit `MathFunctions`, puis cliquez sur **afficher le Code**. Le **éditeur de Code** s’affiche.  
  
7.  Ajoutez une variable locale pour contenir la valeur de propriété :  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Ajoutez la propriété `Let` et la propriété `Get` les procédures de propriété :  
  
    ```  
    Public Property Let Prop1(ByVal vData As Integer)  
       'Used when assigning a value to the property.  
       mvarProp1 = vData  
    End Property  
    Public Property Get Prop1() As Integer  
       'Used when retrieving a property's value.  
       Prop1 = mvarProp1  
    End Property  
    ```  
  
9. Ajoutez une fonction :  
  
    ```  
    Function AddNumbers(   
       ByVal SomeNumber As Integer,   
       ByVal AnotherNumber As Integer) As Integer  
  
       AddNumbers = SomeNumber + AnotherNumber  
    End Function  
    ```  
  
10. Créez et inscrivez l’objet COM en cliquant sur **Créer ComObject1.dll** sur la **fichier** menu.  
  
    > [!NOTE]
    >  Bien que vous pouvez également exposer une classe créée avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] comme un objet COM, il n’est pas un véritable objet COM et ne peut pas être utilisé dans cette procédure pas à pas. Pour plus d’informations, consultez [interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## <a name="interop-assemblies"></a>Assemblys d’interopérabilité  
 Dans la procédure suivante, vous allez créer un assembly d’interopérabilité qui sert de pont entre le code non managé (par exemple, un objet COM) et le code managé [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs_md.md)] utilise. L’assembly d’interopérabilité qui [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] crée gère de nombreux détails de l’utilisation de COM d’objets, tels que *le marshaling d’interopérabilité*, le processus empaqueter des paramètres et valeurs de retour dans les données équivalent types lors de leur déplacement vers et depuis des objets COM. La référence dans le [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] application pointe vers l’assembly d’interopérabilité, pas l’objet COM réel.  
  
#### <a name="to-use-a-com-object-with-visual-basic-2005-and-later-versions"></a>Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures  
  
1.  Ouvrez une nouvelle [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] projet d’Application Windows.  
  
2.  Sur le **projet** menu, cliquez sur **ajouter une référence**.  
  
     Le **ajouter une référence** boîte de dialogue s’affiche.  
  
3.  Sur le **COM** onglet, double-cliquez sur `ComObject1` dans les **nom du composant** et cliquez sur **OK**.  
  
4.  Dans le menu **Projet** , cliquez sur **Ajouter un nouvel élément**.  
  
     Le **ajouter un nouvel élément** boîte de dialogue s’affiche.  
  
5.  Dans le **modèles** volet, cliquez sur **classe**.  
  
     Le nom de fichier par défaut, `Class1.vb`, apparaît dans le **nom** champ. Remplacez ce champ par MathClass.vb et cliquez sur **ajouter**. Cela crée une classe nommée `MathClass`et affiche son code.  
  
6.  Ajoutez le code suivant au début du `MathClass` pour hériter de la classe COM.  
  
     [!code-vb[VbVbalrInterop&#31;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Surcharge de la méthode publique de la classe de base en ajoutant le code suivant à `MathClass`:  
  
     [!code-vb[VbVbalrInterop n°&32;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Étendez la classe héritée en ajoutant le code suivant à `MathClass`:  
  
     [!code-vb[VbVbalrInterop&#33;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 La nouvelle classe hérite des propriétés de la classe de base dans l’objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.  
  
#### <a name="to-test-the-inherited-class"></a>Pour tester la classe héritée  
  
1.  Ajouter un bouton à votre formulaire de démarrage et double-cliquez dessus pour afficher son code.  
  
2.  Dans son `Click` procédure gestionnaire d’événements, ajoutez le code suivant pour créer une instance de `MathClass` et appeler les méthodes surchargées :  
  
     [!code-vb[VbVbalrInterop&#34;](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  Exécutez le projet en appuyant sur F5.  
  
 Lorsque vous cliquez sur le bouton du formulaire, le `AddNumbers` méthode est d’abord appelée avec `Short` numéros, type de données et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] choisit la méthode appropriée à partir de la classe de base. Le deuxième appel à `AddNumbers` est dirigé vers la méthode surchargée à partir de `MathClass`. Le troisième appel appelle le `SubtractNumbers` (méthode), qui étend la classe. La propriété dans la classe de base est définie, et la valeur est affichée.  
  
## <a name="next-steps"></a>Étapes suivantes  
 Vous avez peut-être remarqué que surchargées `AddNumbers` fonction semble avoir les mêmes données de type que la méthode héritée de la classe de base de l’objet COM. Il s’agit, car les arguments et paramètres de la méthode de classe de base sont définis comme des nombres entiers 16 bits dans Visual Basic 6.0, mais sont exposés comme des nombres entiers 16 bits de type `Short` dans les versions ultérieures de Visual Basic. La nouvelle fonction accepte les nombres entiers 32 bits et surcharge la fonction de classe de base.  
  
 Lorsque vous travaillez avec des objets COM, assurez-vous de vérifier la taille et le type des paramètres. Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6.0 en tant qu’argument, vous ne peut pas fournir une collection à partir d’une version ultérieure de Visual Basic.  
  
 Propriétés et méthodes héritées des classes COM peuvent être substituées, ce qui signifie que vous pouvez déclarer une propriété locale ou une méthode qui remplace une propriété ou une méthode héritée d’une classe COM de base. Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution des autres propriétés et méthodes avec les exceptions suivantes :  
  
-   Si vous substituez une propriété ou une méthode héritée d’une classe COM, vous devez remplacer toutes les autres propriétés et méthodes héritées.  
  
-   Les propriétés qui utilisent `ByRef` paramètres ne peut pas être substituées.  
  
## <a name="see-also"></a>Voir aussi  
 [Interopérabilité COM dans les Applications .NET Framework](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits (instruction)](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short (type de données)](../../../visual-basic/language-reference/data-types/short-data-type.md)

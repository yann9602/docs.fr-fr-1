---
title: "Walkthrough: Implementing Inheritance with COM Objects (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "inheritance, COM reusability"
  - "base classes, COM reusability"
  - "inheritance, walkthroughs"
  - "derived classes, COM reusability"
ms.assetid: f8e7263a-de13-48d1-b67c-ca1adf3544d9
caps.latest.revision: 16
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 16
---
# Walkthrough: Implementing Inheritance with COM Objects (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

Vous pouvez dériver des classes Visual Basic à partir de classes `Public` dans des objets COM, même les classes créées avec des versions antérieures de [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  Les propriétés et les méthodes des classes héritées d'objets COM peuvent être substituées ou surchargées comme les propriétés et les méthodes de toute autre classe de base.  L'héritage à partir des objets COM est utile lorsque vous ne voulez pas recompiler une bibliothèque de classes existante.  
  
 La procédure suivante explique comment utiliser Visual Basic 6.0 pour créer un objet COM contenant une classe, puis comment l'utiliser comme classe de base.  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note-settings-general-md.md)]  
  
### Pour générer l'objet COM utilisé dans cette procédure pas à pas  
  
1.  Dans Visual Basic 6.0, ouvrez un nouveau projet de DLL ActiveX.  Un projet nommé `Project1` est créé.  Il a une classe nommée `Class1`.  
  
2.  Dans l'**Explorateur de projets**, cliquez avec le bouton droit sur **Project1**, puis cliquez sur **Propriétés**.  La boîte de dialogue **Propriétés du projet** s'affiche.  
  
3.  Sous l'onglet **Général** de la boîte de dialogue **Propriétés du projet**, modifiez le nom du projet en tapant `ComObject1` dans le champ **Nom de projet**.  
  
4.  Dans l'**Explorateur de projets**, cliquez avec le bouton droit sur `Class1`, puis cliquez sur **Propriétés**.  La fenêtre **Propriétés** de la classe s'affiche.  
  
5.  Affectez la valeur `MathFunctions` à la propriété `Name`.  
  
6.  Dans l'**Explorateur de projets**, cliquez avec le bouton droit sur `MathFunctions`, puis cliquez sur **Afficher le code**.  L'**éditeur de code** s'affiche.  
  
7.  Ajoutez une variable locale pour contenir la valeur de propriété :  
  
    ```  
    ' Local variable to hold property value  
    Private mvarProp1 As Integer  
    ```  
  
8.  Ajoutez les procédures de propriété Property `Let` et Property `Get` :  
  
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
  
10. Créez et inscrivez l'objet OM en cliquant sur **Créer ComObject1.dll** dans le menu **Fichier**.  
  
    > [!NOTE]
    >  Bien que vous puissiez également exposer une classe créée avec [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] comme un objet COM, il ne s'agit pas d'un objet COM réel et il ne peut pas être utilisé dans cette procédure pas à pas.  Pour plus d'informations, consultez [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md).  
  
## Assemblys d'interopérabilité  
 Dans la procédure suivante, vous créez un assembly d'interopérabilité qui sert de pont entre le code non managé \(tel qu'un objet COM\) et le code managé que [!INCLUDE[vsprvs](../../../csharp/includes/vsprvs-md.md)] utilise.  L'assembly d'interopérabilité créé par [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] gère de nombreux détails de l'utilisation d'objets COM, par exemple le *marshaling d'interopérabilité*, le processus qui consiste à empaqueter des paramètres et des valeurs de retour dans des types de données équivalents lors de leurs déplacements vers et à partir des objets COM.  La référence de l'application [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] pointe vers l'assembly d'interopérabilité et non vers l'objet COM réel.  
  
#### Pour utiliser un objet COM avec Visual Basic 2005 et versions ultérieures  
  
1.  Ouvrez un nouveau projet d'application Windows [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)].  
  
2.  Dans le menu **Projet**, cliquez sur **Ajouter une référence**.  
  
     La boîte de dialogue **Ajouter une référence** s'affiche.  
  
3.  Sous l'onglet **COM**, double\-cliquez sur `ComObject1` dans la liste **Nom du composant** et cliquez sur **OK**.  
  
4.  Dans le menu **Projet**, cliquez sur **Ajouter un nouvel élément**.  
  
     La boîte de dialogue **Ajouter un nouvel élément** s'affiche.  
  
5.  Dans le volet **Modèles**, cliquez sur **Classe**.  
  
     Le nom de fichier par défaut, `Class1.vb`, s'affiche dans le champ **Nom**.  Remplacez ce champ par MathClass.vb et cliquez sur **Ouvrir**.  Cela crée une classe nommée `MathClass` et affiche son code.  
  
6.  Ajoutez le code suivant en haut de `MathClass` pour hériter de la classe COM.  
  
     [!code-vb[VbVbalrInterop#31](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_1.vb)]  
  
7.  Surchargez la méthode publique de la classe de base en ajoutant le code suivant à `MathClass` :  
  
     [!code-vb[VbVbalrInterop#32](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_2.vb)]  
  
8.  Étendez la classe héritée en ajoutant le code suivant à `MathClass` :  
  
     [!code-vb[VbVbalrInterop#33](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_3.vb)]  
  
 La nouvelle classe hérite des propriétés de la classe de base dans l'objet COM, surcharge une méthode et définit une nouvelle méthode pour étendre la classe.  
  
#### Pour tester la classe héritée  
  
1.  Ajoutez un bouton à votre formulaire de départ, puis double\-cliquez dessus pour afficher son code.  
  
2.  Dans la procédure de gestionnaire d'événements `Click` du bouton, ajoutez le code suivant pour créer une instance de `MathClass` et appeler les méthodes surchargées :  
  
     [!code-vb[VbVbalrInterop#34](../../../visual-basic/programming-guide/com-interop/codesnippet/VisualBasic/walkthrough-implementing-inheritance-with-com-objects_4.vb)]  
  
3.  Exécutez le projet en appuyant sur F5.  
  
 Lorsque vous cliquez sur le bouton du formulaire, la méthode `AddNumbers` est d'abord appelée avec des nombres de types de données `Short` et [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] choisit la méthode appropriée à partir de la classe de base.  Le second appel à `AddNumbers` est dirigé vers la méthode surchargée à partir de `MathClass`.  Le troisième appel s'adresse à la méthode `SubtractNumbers`, qui étend la classe.  La propriété de la classe de base est définie et la valeur s'affiche.  
  
## Étapes suivantes  
 Vous avez peut\-être remarqué que la fonction surchargée `AddNumbers` semble posséder le même type de données que la méthode héritée à partir de la classe de base de l'objet COM.  Ceci est dû au fait que les arguments et paramètres de la méthode de la classe de base sont définis comme des nombres entiers 16 bits dans Visual Basic 6.0, mais sont exposés comme des nombres entiers 16 bits de type `Short` dans les versions ultérieures de Visual Basic.  La nouvelle fonction accepte les nombres entiers de 32 bits et surcharge la fonction de la classe de base.  
  
 Lorsque vous utilisez des objets COM, veillez à vérifier la taille et les types de données des paramètres.  Par exemple, lorsque vous utilisez un objet COM qui accepte un objet de collection Visual Basic 6.0 en tant qu'argument, vous ne pouvez pas fournir de collection à partir d'une version ultérieure de Visual Basic.  
  
 Les propriétés et les méthodes héritées des classes COM peuvent être substituées, ce qui signifie que vous pouvez déclarer une propriété ou une méthode locale qui remplace une propriété ou une méthode héritée d'une classe COM de base.  Les règles de substitution des propriétés COM héritées sont similaires aux règles de substitution des autres propriétés et méthodes, à l'exception des cas suivants :  
  
-   Si vous substituez une propriété ou une méthode héritée d'une classe COM, vous devez également remplacer toutes les autres propriétés et méthodes héritées.  
  
-   Les propriétés qui utilisent des paramètres `ByRef` ne peuvent pas être substituées.  
  
## Voir aussi  
 [COM Interoperability in .NET Framework Applications](../../../visual-basic/programming-guide/com-interop/com-interoperability-in-net-framework-applications.md)   
 [Inherits Statement](../../../visual-basic/language-reference/statements/inherits-statement.md)   
 [Short Data Type](../../../visual-basic/language-reference/data-types/short-data-type.md)
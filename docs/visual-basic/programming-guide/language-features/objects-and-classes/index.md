---
title: "Objects and Classes in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "classes [Visual Basic]"
  - "objects [Visual Basic]"
ms.assetid: c68c5752-1006-46e1-975a-6717b62a42fc
caps.latest.revision: 26
caps.handback.revision: 26
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Objects and Classes in Visual Basic
[!INCLUDE[vs2017banner](../../../../csharp/includes/vs2017banner.md)]

Un *objet* est une combinaison de code et de données qui peut être traitée comme une entité unique.  Un objet peut être une partie d'une application \(telle qu'un contrôle ou un formulaire\)  ou une application dans son intégralité.  
  
 Lorsque vous créez une application [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], vous utilisez constamment des objets.  Vous pouvez utiliser des objets fournis par [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)], tels que les contrôles, les formulaires et les objets d'accès aux données.  Vous pouvez également utiliser des objets d'autres applications, à l'intérieur de votre application [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)].  Vous pouvez même créer vos propres objets et définir des propriétés ainsi que des méthodes supplémentaires pour ces objets.  Les objets se comportent comme des blocs de construction préfabriqués : vous pouvez écrire un fragment de code une seule fois et le réutiliser continuellement.  
  
 Cette rubrique présente les objets en détail.  
  
## Objets et classes  
 Chaque objet en [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] est défini par une *classe*.  Une classe décrit les variables, propriétés, procédures et événements d'un objet.  Les objets sont des instances de classes ; vous pouvez créer autant d'objets que nécessaire dès que vous avez défini une classe.  
  
 Pour comprendre la relation existant entre un objet et sa classe, pensez à celle existant entre un moule à gâteau et des gâteaux.  Le moule à gâteau représente la classe.  Il définit les caractéristiques de chaque gâteau \(sa taille et sa forme, par exemple\).  La classe permet de créer des objets.  Les objets peuvent être comparés aux gâteaux.  
  
 Vous devez créer un objet pour pouvoir accéder à ses membres.  
  
#### Pour créer un objet à partir d'une classe  
  
1.  Déterminez à partir de quelle classe vous souhaitez créer un objet.  
  
2.  Écrivez une [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) pour créer une variable à laquelle vous pouvez assigner une instance de classe.  La variable doit être du type de la classe souhaitée.  
  
    ```  
  
    Dim nextCustomer As customer   
    ```  
  
3.  Ajoutez le mot clé [New Operator](../../../../visual-basic/language-reference/operators/new-operator.md) pour initialiser la variable à une nouvelle instance de la classe.  
  
    ```  
    Dim nextCustomer As New customer  
    ```  
  
4.  Vous pouvez maintenant accéder aux membres de la classe par le biais de la variable objet.  
  
    ```  
  
    nextCustomer.accountNumber = lastAccountNumber + 1  
    ```  
  
> [!NOTE]
>  Si possible, vous devez déclarer la variable comme étant du type classe que vous envisagez de lui assigner.  On appelle cela une *liaison anticipée*.  Si vous ne connaissez pas le type de classe au moment de la compilation, vous pouvez appeler la *liaison tardive* en déclarant la variable comme étant de [Object Data Type](../../../../visual-basic/language-reference/data-types/object-data-type.md).  Toutefois, la liaison tardive peut ralentir les performances et limiter l'accès aux membres de l'objet à l'exécution.  Pour plus d'informations, consultez [Object Variable Declaration](../../../../visual-basic/programming-guide/language-features/variables/object-variable-declaration.md).  
  
### Instances multiples  
 Les objets récemment créés à partir d'une classe sont souvent identiques les uns aux autres.  Cependant, une fois qu'ils existent en tant qu'objets individuels, leurs variables et propriétés peuvent être modifiées indépendamment des autres instances.  Par exemple, si vous ajoutez trois cases à cocher à un formulaire, chacun de ces objets est une instance de la classe <xref:System.Windows.Forms.CheckBox>.  Les objets <xref:System.Windows.Forms.CheckBox> individuels partagent un ensemble commun de caractéristiques et de fonctionnalités \(propriétés, variables, procédures et événements\) définies par la classe.  Cependant, chacun possède un nom qui lui est propre, il peut être activé ou désactivé séparément et placé à un autre emplacement du formulaire.  
  
## Object, membres  
 Un objet est un élément d'une application, représentant une *instance* d'une classe.  Les champs, les propriétés, les méthodes et les événements sont les blocs de construction des objets et constituent leurs *membres*.  
  
### Accès au membre  
 Pour accéder à un membre d'un objet, vous devez spécifier le nom de la variable objet suivi d'un point \(`.`\) et du nom du membre.  L'exemple suivant définit la propriété <xref:System.Windows.Forms.Control.Text%2A> d'un objet <xref:System.Windows.Forms.Label>.  
  
```  
warningLabel.Text = "Data not saved"  
```  
  
#### Liste de membres IntelliSense  
 IntelliSense répertorie les membres d'une classe lorsque vous appelez son option Liste des membres, par exemple lorsque vous tapez un point \(`.`\) comme opérateur d'accès de membre.  Si vous tapez le point après le nom d'une variable déclarée comme une instance de cette classe, IntelliSense répertorie tous les membres d'instance et aucun des membres partagés.  Si vous tapez le point après le nom de la classe lui\-même, IntelliSense répertorie tous les membres partagés et aucun des membres d'instance.  Pour plus d'informations, consultez [Utilisation de la fonctionnalité IntelliSense](/visual-studio/ide/using-intellisense).  
  
### Champs et propriétés  
 Les *champs* et les *propriétés* sont des informations stockées dans un objet.  Vous récupérez et définissez leurs valeurs avec des instructions d'assignation de la même façon que vous récupérez et définissez des variables locales dans une procédure.  L'exemple suivant récupère la propriété <xref:System.Windows.Forms.Control.Width%2A> et définit la propriété <xref:System.Windows.Forms.Control.ForeColor%2A> d'un objet <xref:System.Windows.Forms.Label>.  
  
```  
Dim warningWidth As Integer = warningLabel.Width  
warningLabel.ForeColor = System.Drawing.Color.Red  
```  
  
 Notez qu'un champ porte également le nom de *variable membre*.  
  
 Utilisez des procédures de propriété si :  
  
-   vous devez contrôler quand et comment une valeur est définie ou extraite ;  
  
-   la propriété possède un ensemble bien défini de valeurs devant être validées ;  
  
-   le fait de définir la valeur entraîne une modification perceptible de l'état de l'objet, comme pour une propriété `IsVisible` ;  
  
-   le fait de définir la propriété entraîne la modification d'autres variables internes ou d'autres valeurs d'autres propriétés ;  
  
-   une série d'étapes doivent être réalisées avant que la propriété ne puisse être définie ou extraite.  
  
 Utilisez des champs si :  
  
-   la valeur est d'un type à validation automatique,  comme par exemple lorsqu'une erreur ou la conversion automatique de données a lieu si une valeur différente de `True` ou `False` est assignée à une variable `Boolean` ;  
  
-   toute valeur située dans la plage de valeurs prises en charge par le type de données est valide,  ce qui est le cas pour de nombreuses propriétés du type `Single` ou `Double` ;  
  
-   la propriété est du type de données `String` et s'il n'existe aucune contrainte quant à la taille ou à la valeur de la chaîne.  
  
-   Pour plus d'informations, consultez [Procédures de propriété](../../../../visual-basic/programming-guide/language-features/procedures/property-procedures.md).  
  
### Méthodes  
 Une *méthode* est une action que peut effectuer un objet.  Par exemple, <xref:System.Windows.Forms.ComboBox.ObjectCollection.Add%2A> est une méthode de l'objet <xref:System.Windows.Forms.ComboBox> qui ajoute une nouvelle entrée à une zone de liste.  
  
 L'exemple suivant présente une utilisation de la méthode <xref:System.Windows.Forms.Timer.Start%2A> d'un objet <xref:System.Windows.Forms.Timer>.  
  
```  
Dim safetyTimer As New System.Windows.Forms.Timer  
safetyTimer.Start()  
```  
  
 Notez qu'une méthode est simplement une *procédure* qui est exposée par un objet.  
  
 Pour plus d'informations, consultez [Procedures](../../../../visual-basic/programming-guide/language-features/procedures/index.md).  
  
### Événements  
 Un événement est une action reconnue par un objet, telle qu'un clic de souris ou une pression sur une touche, pour laquelle vous pouvez écrire du code pour y répondre.  Les événements peuvent se produire suite à une action d'un utilisateur ou au code de programme, ou être provoqués par le système.  Le code qui signale un événement *déclenche* l'événement et le code qui y répond *gère* l'événement.  
  
 Vous pouvez également développer vos événements personnalisés déclenchés par vos objets et gérés par d'autres objets.  Pour plus d'informations, consultez [Events](../../../../visual-basic/programming-guide/language-features/events/events.md).  
  
### Membres d'instance et membres partagés  
 Lorsque vous créez un objet à partir d'une classe, le résultat est une instance de cette classe.  Les membres qui ne sont pas déclarés avec le mot clé [Shared](../../../../visual-basic/language-reference/modifiers/shared.md) sont des *membres d'instance*, qui appartiennent strictement à cette instance particulière.  Un membre d'instance dans une instance est indépendant du même membre dans une autre instance de la même classe.  Par exemple, une variable membre d'instance peut avoir des valeurs différentes dans différentes instances.  
  
 Les membres déclarés avec le mot clé  `Shared` sont des *membres partagés*, qui appartiennent à la classe dans son ensemble et non à une instance particulière.  Un membre partagé existe uniquement une fois, quel que soit le nombre d'instances de sa classe que vous créez, ou même si vous ne créez pas d'instance.  Par exemple, une variable membre partagée possède une seule valeur, qui est disponible à tout le code qui peut accéder à la classe.  
  
#### Accès à des membres non partagés  
  
###### Pour accéder à un membre non partagé d'un objet  
  
1.  Assurez\-vous que l'objet a été créé à partir de sa classe et assigné à une variable objet.  
  
    ```  
    Dim secondForm As New System.Windows.Forms.Form  
    ```  
  
2.  Dans l'instruction qui accède au membre, faites suivre le nom de la variable objet de l'*opérateur d'accès de membre* \(`.`\), puis du nom du membre.  
  
    ```  
    secondForm.Show()  
    ```  
  
#### Accès à des membres partagés  
  
###### Pour accéder à un membre partagé d'un objet  
  
-   Faites suivre le nom de classe de l'*opérateur d'accès de membre* \(`.`\), puis du nom du membre.  Vous devez toujours accéder à un membre `Shared` de l'objet directement par le biais du nom de la classe.  
  
    ```  
    MsgBox("This computer is called " & Environment.MachineName)  
    ```  
  
-   Si vous avez déjà créé un objet à partir de la classe, vous pouvez également accéder à un membre `Shared` par le biais de la variable de l'objet.  
  
### Différences entre les classes et les modules  
 La principale différence qu'il existe entre les classes et les modules est que les classes peuvent être instanciées comme des objets, mais pas les modules standard.  Comme il n'existe qu'une seule copie des données d'un module standard, quand une partie de votre programme transforme une variable publique en module standard, toute autre partie du programme reçoit la même valeur si, par la suite, elle lit cette variable.  Par opposition, les données d'objet existent séparément pour chaque objet instancié.  Une autre différence est que les classes peuvent implémenter des interfaces, contrairement aux modules standard.  
  
> [!NOTE]
>  Lorsque le modificateur `Shared` est appliqué à un membre de classe, il est associé à la classe elle\-même au lieu d'une instance particulière de la classe.  Le membre est accessible directement via le nom de la classe au même titre que les membres de module.  
  
 Les classes et les modules utilisent également des portées différentes pour leurs membres.  Les membres définis dans une classe ont comme portée une instance spécifique de la classe et n'existent que pendant la durée de vie de l'objet.  Pour accéder aux membres de classe depuis l'extérieur d'une classe, vous devez utiliser des noms qualifiés complets au format *Objet*.*Membre*.  
  
 En revanche, les membres déclarés dans un module sont publiquement accessibles par défaut et sont accessibles par tout code qui peut accéder au module.  Dès lors, les variables d'un module standard sont effectivement des variables globales puisqu'elles sont visibles à n'importe quel emplacement du projet et qu'elles existent pendant toute la durée de vie du programme.  
  
## Réutilisation des classes et des objets  
 Les objets vous permettent de déclarer une seule fois des variables et des procédures, puis de les réutiliser quand bon vous semble.  Par exemple, pour ajouter un vérificateur d'orthographe à une application, vous pouvez définir toutes les variables et les fonctions de support pour assurer une vérification orthographique.  Si vous créez votre vérificateur d'orthographe sous forme de classe, vous pouvez ensuite le réutiliser dans d'autres applications en ajoutant une référence à l'assembly compilé.  Vous pouvez même utiliser une classe de vérificateur d'orthographe développée par quelqu'un d'autre pour vous éviter tout travail superflu.  
  
 Le [!INCLUDE[dnprdnshort](../../../../csharp/getting-started/includes/dnprdnshort_md.md)] fournit de nombreux exemples de composants disponibles.  L'exemple suivant utilise la classe <xref:System.TimeZone> dans l'espace de noms <xref:System>.  <xref:System.TimeZone> fournit des membres qui vous permettent de récupérer les informations relatives au fuseau horaire du système informatique actuel.  
  
```  
Public Sub examineTimeZone()  
    Dim tz As System.TimeZone = System.TimeZone.CurrentTimeZone  
    Dim s As String = "Current time zone is "  
    s &= CStr(tz.GetUtcOffset(Now).Hours) & " hours and "  
    s &= CStr(tz.GetUtcOffset(Now).Minutes) & " minutes "  
    s &= "different from UTC (coordinated universal time)"  
    s &= vbCrLf & "and is currently "  
    If tz.IsDaylightSavingTime(Now) = False Then s &= "not "  
    s &= "on ""summer time""."  
    MsgBox(s)  
End Sub  
```  
  
 Dans l'exemple précédent, la première instruction Dim \([Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md)\) déclare une variable objet de type <xref:System.TimeZone> et lui assigne un objet <xref:System.TimeZone> retourné par la propriété <xref:System.TimeZone.CurrentTimeZone%2A>.  
  
## Relations entre les objets  
 Les objets peuvent être reliés les uns aux autres de diverses manières.  Les principales sortes de relations sont les relations *hiérarchiques* et les relations *contenant\-contenu*.  
  
### Relation hiérarchique  
 Lorsque des classes sont dérivées de classes plus fondamentales, on dit qu'elles ont une *relation hiérarchique*.  Les hiérarchies de classe sont utiles lors d'une description d'éléments qui représentent un sous\-type d'une classe plus générale.  
  
 Dans l'exemple suivant, supposez que vous souhaitez définir un genre spécial de <xref:System.Windows.Forms.Button> qui agit comme un <xref:System.Windows.Forms.Button> normal, mais qui expose également une méthode qui inverse les couleurs de premier plan et d'arrière\-plan.  
  
##### Pour définir une classe dérivée d'une classe existante  
  
1.  Utilisez une [Class Statement](../../../../visual-basic/language-reference/statements/class-statement.md) pour définir une classe à partir de laquelle créer l'objet dont vous avez besoin.  
  
     `Public Class reversibleButton`  
  
     Assurez\-vous qu'une instruction `End Class` suit la dernière ligne de code dans votre classe.  Par défaut, l'environnement de développement intégré \(IDE\) génère automatiquement une instruction `End Class` lorsque vous entrez une instruction `Class`.  
  
2.  Faites suivre immédiatement l'instruction `Class` d'une [Inherits Statement](../../../../visual-basic/language-reference/statements/inherits-statement.md).  Spécifiez la classe à partir de laquelle dérive votre nouvelle classe.  
  
     `Inherits System.Windows.Forms.Button`  
  
     Votre nouvelle classe hérite de tous les membres définis par la classe de base.  
  
3.  Ajoutez le code pour les membres supplémentaires exposés par votre classe dérivée.  Par exemple, vous pourriez ajouter une méthode `reverseColors` et votre classe dérivée pourrait ressembler à ce qui suit :  
  
    ```  
    Public Class reversibleButton  
        Inherits System.Windows.Forms.Button  
        Public Sub reverseColors()   
            Dim saveColor As System.Drawing.Color = Me.BackColor  
            Me.BackColor = Me.ForeColor  
            Me.ForeColor = saveColor  
        End Sub  
    End Class   
    ```  
  
     Si vous créez un objet à partir de la classe `reversibleButton`, il peut accéder à tous les membres de la classe <xref:System.Windows.Forms.Button>, ainsi qu'à la méthode `reverseColors` et à tout autre nouveau membre que vous définissez sur `reversibleButton`.  
  
 Dans la mesure où les classes dérivées héritent des membres de la classe dont elles sont issues, elles peuvent devenir plus complexes au fur et à mesure que vous avancez dans une hiérarchie de classe.  Pour plus d'informations, consultez [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
#### Compilation du code  
 Assurez\-vous que le compilateur peut accéder à la classe à partir de laquelle vous envisagez de dériver votre nouvelle classe.  Cela peut signifier qualifier complètement son nom, comme dans l'exemple précédent ou identifier son espace de noms dans une [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md).  Si la classe est dans un projet différent, vous devrez peut\-être ajouter une référence à ce projet.  Pour plus d'informations, consultez [Gestion des références dans un projet](/visual-studio/ide/managing-references-in-a-project).  
  
### Relation contenant\-contenu  
 Les objets peuvent également entretenir une *relation contenant\-contenu*.  Les objets conteneurs encapsulent d'autres objets.  Par exemple, l'objet <xref:System.OperatingSystem> contient logiquement un objet <xref:System.Version>, qu'il retourne par le biais de sa propriété <xref:System.OperatingSystem.Version%2A>.  Notez que l'objet conteneur ne contient pas physiquement d'autre objet.  
  
#### Regroupements  
 Les *collections* représentent un type particulier de relation contenant\-contenu d'un objet.  Les collections sont des groupes d'objets similaires qui peuvent être énumérés.  [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] prend en charge une syntaxe spécifique dans l'instruction For Each...Next \([For Each...Next, instruction](../../../../visual-basic/language-reference/statements/for-each-next-statement.md)\) qui vous permet d'effectuer une itération au sein des éléments d'une collection.  En outre, les collections vous permettent souvent d'utiliser une <xref:Microsoft.VisualBasic.Collection.Item%2A> pour extraire des éléments par leur index ou en les associant à une chaîne unique.  Les collections peuvent être plus simples à utiliser que les tableaux car elles vous permettent d'ajouter ou d'enlever des éléments sans utiliser d'index.  Grâce à leur simplicité d'utilisation, elles sont souvent utilisées pour stocker des formulaires et des contrôles.  
  
## Rubriques connexes  
 [Walkthrough: Defining Classes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/walkthrough-defining-classes.md)  
 Fournit une description pas à pas de la création d'une classe.  
  
 [Overloaded Properties and Methods](../../../../visual-basic/programming-guide/language-features/objects-and-classes/overloaded-properties-and-methods.md)  
 Propriétés et méthodes surchargées  
  
 [Inheritance Basics](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 Présente les modificateurs d'héritage, les méthodes de substitution et les propriétés, MyClass et MyBase.  
  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)  
 Analyse la création et la suppression des instances de classe.  
  
 [Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md)  
 Décrit comment créer et utiliser des types anonymes, pour créer des objets sans écrire de définition de classe pour le type de données.  
  
 [Object Initializers: Named and Anonymous Types](../../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)  
 Discute des initialiseurs d'objets, permettant de créer des instances de types nommés et anonymes en utilisant une expression unique.  
  
 [Comment : déduire les types et les noms de propriétés dans des déclarations de types anonymes](../../../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-infer-property-names-and-types-in-anonymous-type-declarations.md)  
 Explique comment déduire les types et les noms de propriétés dans des déclarations de types anonymes.  Fournit des exemples d'inférences ayant réussi et échoué.
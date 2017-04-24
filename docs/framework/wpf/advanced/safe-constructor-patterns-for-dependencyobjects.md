---
title: "Mod&#232;les de constructeur s&#233;curis&#233; pour DependencyObjects | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "modèles de constructeur pour les objets de dépendance"
  - "objets de dépendance, modèles de constructeur"
  - "FXCop (outil)"
ms.assetid: f704b81c-449a-47a4-ace1-9332e3cc6d60
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# Mod&#232;les de constructeur s&#233;curis&#233; pour DependencyObjects
En général, les constructeurs de classe ne doivent pas appeler des rappels, tels que des méthodes virtuelles ou des délégués, car les constructeurs peuvent être appelés comme initialisation de base des constructeurs pour une classe dérivée.  L'entrée de la méthode virtuelle peut être effectuée lorsqu'un objet a un état d'initialisation incomplet.  Toutefois, le système de propriétés lui\-même appelle et expose en interne des rappels dans le cadre du système de propriétés de dépendance.  Une opération aussi simple que définir une valeur de propriété de dépendance avec un appel à <xref:System.Windows.DependencyObject.SetValue%2A> inclut potentiellement un rappel quelque part dans la détermination.  Pour cette raison, vous devez définir les valeurs des propriétés de dépendance avec précaution dans le corps d'un constructeur, ce qui peut devenir problématique si le type est utilisé comme classe de base.  Il existe un modèle spécifique pour implémenter des constructeurs <xref:System.Windows.DependencyObject>, qui évite des problèmes spécifiques liés aux états de propriété de dépendance et aux rappels inhérents. Ce modèle est documenté ici.  
  
   
  
<a name="Property_System_Virtual_Methods"></a>   
## Méthodes virtuelles de système de propriétés  
 Les méthodes virtuelles ou rappels suivants sont appelés potentiellement au cours des calculs de l'appel à <xref:System.Windows.DependencyObject.SetValue%2A> qui définit une valeur de propriété de dépendance : <xref:System.Windows.ValidateValueCallback>, <xref:System.Windows.PropertyChangedCallback>, <xref:System.Windows.CoerceValueCallback>, <xref:System.Windows.DependencyObject.OnPropertyChanged%2A>.  Chacune de ces méthodes virtuelles ou chacun de ces rappels a une fonction spécifique pour étendre la souplesse du système de propriétés et des propriétés de dépendance [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].  Pour plus d'informations sur l'utilisation de ces méthodes virtuelles pour personnaliser la détermination des valeurs des propriétés, consultez [Validation et rappels de propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md).  
  
### Mise en application de la règle FXCop etméthodes virtuelles de système de propriétés  
 Si vous utilisez l'outil Microsoft FXCop dans le cadre du processus de génération et que vous dérivez des classes depuis des classes ou certaines classes d'infrastructure [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] qui appellent le constructeur de base, ou implémentez vos propres propriétés de dépendance dans des classes dérivées, vous pouvez être confronté à une violation de règle FXCop.  La chaîne de nom de cette violation est :  
  
 `DoNotCallOverridableMethodsInConstructors`  
  
 Il s'agit d'une règle qui fait partie de l'ensemble de règles publiques par défaut de FXCop.  Cette règle peut signaler une trace via le système de propriétés de dépendance qui appelle une méthode virtuelle de système de propriété de dépendance.  Cette violation de règle peut continuer d'apparaître même après avoir respecté les modèles de constructeur recommandés documentés dans cette rubrique. Par conséquent, il se peut que vous deviez désactiver ou supprimer cette règle dans la configuration de l'ensemble de règles FXCop.  
  
### La plupart des problèmes proviennent des classes dérivées et non pas de l'utilisation des classes  
 Les problèmes signalés par cette règle se produisent lorsqu'une classe que vous implémentez avec des méthodes virtuelles dans sa séquence de construction est ensuite utilisée dans une dérivation de classe.  Si vous scellez la classe ou savez ou faites en sorte que la classe ne soit pas utilisée dans une dérivation de classe, alors les explications fournies ici et les problèmes qui ont motivé la règle FXCop ne s'appliquent pas.  Toutefois, si vous créez des classes pour les utiliser comme des classes de base \(si vous créez des modèles ou un groupe de bibliothèques développables, par exemple\) suivez les modèles recommandés ici concernant les constructeurs.  
  
### Les constructeurs par défaut doivent initialiser toutes les valeurs demandées par les rappels  
 Les membres d'instances utilisés par les remplacements de classe ou les rappels \(les rappels de la liste dans la section des méthodes virtuelles de système de propriétés\) doivent être initialisés dans le constructeur par défaut de classe, même si certaines de ces valeurs sont remplies par de "vraies" valeurs via des paramètres des constructeurs non définis par défaut.  
  
 L'exemple de code suivant \(et les exemples suivants\) est un exemple de pseudo\-code C\# qui viole cette règle et explique le problème :  
  
```  
public class MyClass : DependencyObject  
{  
    public MyClass() {}  
    public MyClass(object toSetWobble)  
        : this()  
    {  
        Wobble = toSetWobble; //this is backed by a DependencyProperty  
        _myList = new ArrayList();    // this line should be in the default ctor  
    }  
    public static readonly DependencyProperty WobbleProperty =   
        DependencyProperty.Register("Wobble", typeof(object), typeof(MyClass));  
    public object Wobble  
    {  
        get { return GetValue(WobbleProperty); }  
        set { SetValue(WobbleProperty, value); }  
    }  
    protected override void OnPropertyChanged(DependencyPropertyChangedEventArgs e)  
    {  
        int count = _myList.Count;    // null-reference exception  
    }  
    private ArrayList _myList;  
}  
```  
  
 Lorsque le code d'application appelle `new MyClass(objectvalue)`, le constructeur par défaut et les constructeurs de classes par défaut sont appelés.  Il définit ensuite `Property1 = object1` qui appelle la méthode virtuelle `OnPropertyChanged` dans le <xref:System.Windows.DependencyObject> `MyClass` propriétaire.  La substitution fait référence à `_myList` qui n'a pas encore été initialisé.  
  
 Une façon d'éviter ces problèmes consiste à s'assurer que les rappels utilisent uniquement d'autres propriétés de dépendance et que chacune de ces propriétés de dépendance a une valeur par défaut définie dans ses métadonnées enregistrées.  
  
<a name="Safe_Constructor_Patterns"></a>   
## Modèles de constructeur sécurisé  
 Pour éviter les risques d'initialisation incomplète si la classe est utilisée comme une classe de base, suivez ces modèles :  
  
#### Constructeurs par défaut qui appellent l'initialisation de base  
 Implémentez ces constructeurs en appelant la valeur par défaut de base :  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass() : base() {  
        // ALL class initialization, including initial defaults for   
        // possible values that other ctors specify or that callbacks need.  
    }  
}  
```  
  
#### Constructeurs non définis par défaut \(commodité\) qui ne font pas correspondre des signatures de base  
 Si ces constructeurs utilisent les paramètres pour définir des propriétés de dépendance dans l'initialisation, appelez en premier votre propre constructeur par défaut de classe pour l'initialisation, puis utilisez les paramètres pour définir les propriétés de dépendance.  Il peut s'agir de propriétés de dépendance définies par la classe ou de propriétés de dépendance héritées des classes de base, mais dans l'un ou l'autre cas utilisez le modèle suivant :  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### Constructeurs non définis par défaut \(commodité\) qui font correspondre des signatures de base  
 Au lieu d'appeler le constructeur de base avec le même paramétrage, appelez de nouveau votre propre constructeur par défaut de classe.  N'appelez pas l'initialiseur de base, mais `this()`.  Reproduisez ensuite le comportement du constructeur d'origine en utilisant les paramètres passés comme valeurs pour définir les propriétés pertinentes.  Utilisez la documentation du constructeur de base d'origine pour déterminer les propriétés que les paramètres sont sensés définir :  
  
```  
public MyClass : SomeBaseClass {  
    public MyClass(object toSetProperty1) : this() {  
        // Class initialization NOT done by default.  
        // Then, set properties to values as passed in ctor parameters.  
        Property1 = toSetProperty1;  
    }  
}  
```  
  
#### Doit faire correspondre toutes les signatures  
 Si le type de base a plusieurs signatures, vous devez faire correspondre toutes les signatures possibles à une implémentation de votre constructeur qui utilise le modèle recommandé d'appel du constructeur par défaut de classe avant de définir d'autres propriétés.  
  
#### Définition des propriétés de dépendance avec SetValue  
 Ces mêmes modèles s'appliquent si vous définissez une propriété qui n'a pas de wrapper pour faciliter la définition des propriétés et que vous définissez les valeurs avec <xref:System.Windows.DependencyObject.SetValue%2A>.  Vos appels à <xref:System.Windows.DependencyObject.SetValue%2A> qui traversent des paramètres de constructeur doivent également appeler le constructeur par défaut de la classe pour l'initialisation.  
  
## Voir aussi  
 [Propriétés de dépendance personnalisées](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)   
 [Vue d'ensemble des propriétés de dépendance](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)   
 [Sécurité de propriété de dépendance](../../../../docs/framework/wpf/advanced/dependency-property-security.md)
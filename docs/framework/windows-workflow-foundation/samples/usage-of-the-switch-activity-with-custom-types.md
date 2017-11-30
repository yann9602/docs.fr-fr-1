---
title: "Utilisation de l'activité Switch avec des types personnalisés"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 482a48c4-eb83-40c3-a4e2-2f9a8af88b75
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 57a6a15f648f83a60f3ac402443c3c5e4aecfcd4
ms.sourcegitcommit: 5177d6ae2e9baf026f07ee0631556700a5a193f7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a><span data-ttu-id="ee590-102">Utilisation de l'activité Switch avec des types personnalisés</span><span class="sxs-lookup"><span data-stu-id="ee590-102">Usage of the Switch Activity with Custom Types</span></span>
<span data-ttu-id="ee590-103">Cet exemple montre comment permettre à une activité <xref:System.Activities.Statements.Switch%601> d'évaluer un type complexe défini par l'utilisateur au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ee590-103">This sample describes how to enable a <xref:System.Activities.Statements.Switch%601> activity to evaluate a user-defined complex type at runtime.</span></span> <span data-ttu-id="ee590-104">Dans les langages de programmation procéduraux traditionnels, un [commutateur](http://go.microsoft.com/fwlink/?LinkId=180521) instruction sélectionne une logique d’exécution en fonction de l’évaluation conditionnelle d’une variable.</span><span class="sxs-lookup"><span data-stu-id="ee590-104">In most traditional procedural programming languages, a [switch](http://go.microsoft.com/fwlink/?LinkId=180521) statement selects an execution logic based on the conditional evaluation of a variable.</span></span> <span data-ttu-id="ee590-105">D'ordinaire, une instruction `switch` opère sur une expression qui peut être évaluée statiquement.</span><span class="sxs-lookup"><span data-stu-id="ee590-105">Traditionally, a `switch` statement operates on an expression that can be statically evaluated.</span></span> <span data-ttu-id="ee590-106">Par exemple, en C#, cela signifie que seuls des types primitifs, tels que <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, et des types énumération sont pris en charge.</span><span class="sxs-lookup"><span data-stu-id="ee590-106">For example, in C# this means that only primitive types, such as <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, and enumeration types are supported.</span></span>  
  
 <span data-ttu-id="ee590-107">Pour permettre la commutation sur une classe personnalisée, la logique doit être implémentée pour évaluer les valeurs du type complexe personnalisé au moment de l'exécution.</span><span class="sxs-lookup"><span data-stu-id="ee590-107">To enable switching on a custom class, logic must be implemented to evaluate values of the custom complex type at runtime.</span></span> <span data-ttu-id="ee590-108">Cet exemple montre comment permettre la commutation sur un type complexe personnalisé nommé `Person`.</span><span class="sxs-lookup"><span data-stu-id="ee590-108">This sample demonstrates how to enable switching on a custom complex type named `Person`.</span></span>  
  
-   <span data-ttu-id="ee590-109">Dans la classe personnalisée `Person`, un attribut <xref:System.ComponentModel.TypeConverter> est déclaré avec le nom du <xref:System.ComponentModel.TypeConverter> personnalisé.</span><span class="sxs-lookup"><span data-stu-id="ee590-109">In the custom class `Person`, a <xref:System.ComponentModel.TypeConverter> attribute is declared with the name of the custom <xref:System.ComponentModel.TypeConverter>.</span></span>  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   <span data-ttu-id="ee590-110">Dans la classe personnalisée `Person`, les classes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> sont remplacées.</span><span class="sxs-lookup"><span data-stu-id="ee590-110">In the custom class `Person`, the <xref:System.Object.Equals%2A> and <xref:System.Object.GetHashCode%2A> classes are overridden.</span></span>  
  
    ```  
    public override bool Equals(object obj)  
    {  
        Person person = obj as Person;  
  
        if (person != null)  
        {  
            return string.Equals(this.Name, person.Name);  
        }  
  
        return false;  
    }  
  
    public override int GetHashCode()  
    {  
        if (this.Name != null)  
        {  
            return this.Name.GetHashCode();  
        }  
  
        return 0;  
    }  
    ```  
  
-   <span data-ttu-id="ee590-111">Une classe <xref:System.ComponentModel.TypeConverter> personnalisée qui effectue la conversion d'une instance de la classe personnalisée en chaîne et d'une chaîne en instance d'une classe personnalisée est implémentée.</span><span class="sxs-lookup"><span data-stu-id="ee590-111">A custom <xref:System.ComponentModel.TypeConverter> class is implemented that performs the conversion of an instance of the custom class to a string and a string to an instance of a custom class.</span></span>  
  
    ```  
    public class PersonConverter : TypeConverter  
    {  
        public override bool CanConvertFrom(ITypeDescriptorContext context,  
           Type sourceType)  
        {  
            return (sourceType is string);  
        }  
  
        // Overrides the ConvertFrom method of TypeConverter.  
        public override object ConvertFrom(ITypeDescriptorContext context,  
           CultureInfo culture, object value)  
        {  
            if (value == null)  
            {  
                return null;  
            }  
  
            if (value is string)  
            {  
                return new Person  
                {  
                    Name = (string)value  
                };  
            }  
  
            return base.ConvertFrom(context, culture, value);  
        }  
  
        // Overrides the ConvertTo method of TypeConverter.  
        public override object ConvertTo(ITypeDescriptorContext context,  
           CultureInfo culture, object value, Type destinationType)  
        {  
            if (destinationType == typeof(string))  
            {  
                if (value != null)  
                {  
                    return ((Person) value).Name;  
                }  
                else  
                {  
                    return null;  
                }  
            }  
  
            return base.ConvertTo(context, culture, value, destinationType);  
        }  
    }  
    ```  
  
 <span data-ttu-id="ee590-112">Les fichiers suivants sont inclus dans cet exemple :</span><span class="sxs-lookup"><span data-stu-id="ee590-112">The following files are included in this sample:</span></span>  
  
-   <span data-ttu-id="ee590-113">**Person.cs**: définit la `Person` classe.</span><span class="sxs-lookup"><span data-stu-id="ee590-113">**Person.cs**: Defines the `Person` class.</span></span>  
  
-   <span data-ttu-id="ee590-114">**PersonConverter.cs**: le convertisseur de type pour la `Person` classe.</span><span class="sxs-lookup"><span data-stu-id="ee590-114">**PersonConverter.cs**: The type converter for the `Person` class.</span></span>  
  
-   <span data-ttu-id="ee590-115">**Sequence.XAML**: un workflow qui bascule vers le `Person` type.</span><span class="sxs-lookup"><span data-stu-id="ee590-115">**Sequence.xaml**: a workflow that switches over the `Person` type.</span></span>  
  
-   <span data-ttu-id="ee590-116">**Program.cs**: la fonction principale qui exécute le flux de travail.</span><span class="sxs-lookup"><span data-stu-id="ee590-116">**Program.cs**: The main function that runs the workflow.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ee590-117">Pour utiliser cet exemple</span><span class="sxs-lookup"><span data-stu-id="ee590-117">To use this sample</span></span>  
  
1.  <span data-ttu-id="ee590-118">Chargez Switch.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="ee590-118">Load Switch.sln in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="ee590-119">Appuyez sur Ctrl+Maj+B pour générer la solution.</span><span class="sxs-lookup"><span data-stu-id="ee590-119">Press CTRL+SHIFT+B to build the solution.</span></span>  
  
3.  <span data-ttu-id="ee590-120">Appuyez sur CTRL+F5 pour exécuter l'exemple.</span><span class="sxs-lookup"><span data-stu-id="ee590-120">Press CTRL + F5 to run the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ee590-121">Les exemples peuvent déjà être installés sur votre ordinateur.</span><span class="sxs-lookup"><span data-stu-id="ee590-121">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ee590-122">Recherchez le répertoire (par défaut) suivant avant de continuer.</span><span class="sxs-lookup"><span data-stu-id="ee590-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ee590-123">Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] .</span><span class="sxs-lookup"><span data-stu-id="ee590-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ee590-124">Cet exemple se trouve dans le répertoire suivant.</span><span class="sxs-lookup"><span data-stu-id="ee590-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a><span data-ttu-id="ee590-125">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="ee590-125">See Also</span></span>  
 [<span data-ttu-id="ee590-126">Bibliothèque d’activités intégrée</span><span class="sxs-lookup"><span data-stu-id="ee590-126">Built-In Activity Library</span></span>](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)

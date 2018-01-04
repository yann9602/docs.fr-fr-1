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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61485a59ae3af17bef58c0fccbe062c8b9171a34
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/22/2017
---
# <a name="usage-of-the-switch-activity-with-custom-types"></a>Utilisation de l'activité Switch avec des types personnalisés
Cet exemple montre comment permettre à une activité <xref:System.Activities.Statements.Switch%601> d'évaluer un type complexe défini par l'utilisateur au moment de l'exécution. Dans les langages de programmation procéduraux traditionnels, un [commutateur](http://go.microsoft.com/fwlink/?LinkId=180521) instruction sélectionne une logique d’exécution en fonction de l’évaluation conditionnelle d’une variable. D'ordinaire, une instruction `switch` opère sur une expression qui peut être évaluée statiquement. Par exemple, en C#, cela signifie que seuls des types primitifs, tels que <xref:System.Boolean>, <xref:System.Int32>, <xref:System.String>, et des types énumération sont pris en charge.  
  
 Pour permettre la commutation sur une classe personnalisée, la logique doit être implémentée pour évaluer les valeurs du type complexe personnalisé au moment de l'exécution. Cet exemple montre comment permettre la commutation sur un type complexe personnalisé nommé `Person`.  
  
-   Dans la classe personnalisée `Person`, un attribut <xref:System.ComponentModel.TypeConverter> est déclaré avec le nom du <xref:System.ComponentModel.TypeConverter> personnalisé.  
  
    ```  
    [TypeConverter(typeof(PersonConverter))]  
    public class Person  
    {  
       public string Name { get; set; }  
       public int Age { get; set; }  
    ...  
    ```  
  
-   Dans la classe personnalisée `Person`, les classes <xref:System.Object.Equals%2A> et <xref:System.Object.GetHashCode%2A> sont remplacées.  
  
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
  
-   Une classe <xref:System.ComponentModel.TypeConverter> personnalisée qui effectue la conversion d'une instance de la classe personnalisée en chaîne et d'une chaîne en instance d'une classe personnalisée est implémentée.  
  
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
  
 Les fichiers suivants sont inclus dans cet exemple :  
  
-   **Person.cs**: définit la `Person` classe.  
  
-   **PersonConverter.cs**: le convertisseur de type pour la `Person` classe.  
  
-   **Sequence.XAML**: un workflow qui bascule vers le `Person` type.  
  
-   **Program.cs**: la fonction principale qui exécute le flux de travail.  
  
#### <a name="to-use-this-sample"></a>Pour utiliser cet exemple  
  
1.  Chargez Switch.sln dans [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Appuyez sur Ctrl+Maj+B pour générer la solution.  
  
3.  Appuyez sur CTRL+F5 pour exécuter l'exemple.  
  
> [!IMPORTANT]
>  Les exemples peuvent déjà être installés sur votre ordinateur. Recherchez le répertoire (par défaut) suivant avant de continuer.  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Si ce répertoire n’existe pas, accédez à la page [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) pour télécharger tous les exemples [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] et [!INCLUDE[wf1](../../../../includes/wf1-md.md)] . Cet exemple se trouve dans le répertoire suivant.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Switch`  
  
## <a name="see-also"></a>Voir aussi  
 [Bibliothèque d’activités intégrée](../../../../docs/framework/windows-workflow-foundation/net-framework-4-5-built-in-activity-library.md)

---
title: "Utilisation de la variance dans les interfaces pour les collections génériques (C#)"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: a44f0708-10fa-4c76-82cd-daa6e6b31e8e
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5d505b566fe604afdedea583dc8c001f80c15d3c
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="using-variance-in-interfaces-for-generic-collections-c"></a>Utilisation de la variance dans les interfaces pour les collections génériques (C#)
Une interface covariante permet à ses méthodes de retourner des types plus dérivés que ceux spécifiés dans l’interface. Une interface contravariante permet à ses méthodes d’accepter des paramètres de types moins dérivés que ceux spécifiés dans l’interface.  
  
 Dans .NET Framework 4, plusieurs interfaces existantes sont devenues covariantes et contravariantes. Celles-ci comprennent <xref:System.Collections.Generic.IEnumerable%601> et <xref:System.IComparable%601>. Cela vous permet de réutiliser des méthodes qui fonctionnent avec les collections génériques de types de base pour les collections de types dérivés.  
  
 Pour obtenir la liste des interfaces de type variant dans le .NET Framework, consultez [Variance dans les interfaces génériques (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md).  
  
## <a name="converting-generic-collections"></a>Conversion de collections génériques  
 L’exemple suivant illustre les avantages de la prise en charge de la covariance dans l’interface <xref:System.Collections.Generic.IEnumerable%601>. La méthode `PrintFullName` accepte une collection de type `IEnumerable<Person>` comme paramètre. Toutefois, vous pouvez la réutiliser pour une collection de type `IEnumerable<Employee>`, car `Employee` hérite de `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
class Program  
{  
    // The method has a parameter of the IEnumerable<Person> type.  
    public static void PrintFullName(IEnumerable<Person> persons)  
    {  
        foreach (Person person in persons)  
        {  
            Console.WriteLine("Name: {0} {1}",  
            person.FirstName, person.LastName);  
        }  
    }  
  
    public static void Test()  
    {  
        IEnumerable<Employee> employees = new List<Employee>();  
  
        // You can pass IEnumerable<Employee>,   
        // although the method expects IEnumerable<Person>.  
  
        PrintFullName(employees);  
  
    }  
}  
```  
  
## <a name="comparing-generic-collections"></a>Comparaison de collections génériques  
 L’exemple suivant illustre les avantages de la prise en charge de la contravariance dans l’interface <xref:System.Collections.Generic.IComparer%601>. La classe `PersonComparer` implémente l'interface `IComparer<Person>`. Toutefois, vous pouvez réutiliser cette classe pour comparer une séquence d’objets de type `Employee`, car `Employee` hérite de `Person`.  
  
```csharp  
// Simple hierarchy of classes.  
public class Person  
{  
    public string FirstName { get; set; }  
    public string LastName { get; set; }  
}  
  
public class Employee : Person { }  
  
// The custom comparer for the Person type  
// with standard implementations of Equals()  
// and GetHashCode() methods.  
class PersonComparer : IEqualityComparer<Person>  
{  
    public bool Equals(Person x, Person y)  
    {              
        if (Object.ReferenceEquals(x, y)) return true;  
        if (Object.ReferenceEquals(x, null) ||  
            Object.ReferenceEquals(y, null))  
            return false;              
        return x.FirstName == y.FirstName && x.LastName == y.LastName;  
    }  
    public int GetHashCode(Person person)  
    {  
        if (Object.ReferenceEquals(person, null)) return 0;  
        int hashFirstName = person.FirstName == null  
            ? 0 : person.FirstName.GetHashCode();  
        int hashLastName = person.LastName.GetHashCode();  
        return hashFirstName ^ hashLastName;  
    }  
}  
  
class Program  
{  
  
    public static void Test()  
    {  
        List<Employee> employees = new List<Employee> {  
               new Employee() {FirstName = "Michael", LastName = "Alexander"},  
               new Employee() {FirstName = "Jeff", LastName = "Price"}  
            };  
  
        // You can pass PersonComparer,   
        // which implements IEqualityComparer<Person>,  
        // although the method expects IEqualityComparer<Employee>.  
  
        IEnumerable<Employee> noduplicates =  
            employees.Distinct<Employee>(new PersonComparer());  
  
        foreach (var employee in noduplicates)  
            Console.WriteLine(employee.FirstName + " " + employee.LastName);  
    }  
}  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Variance dans les interfaces génériques (C#)](../../../../csharp/programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)


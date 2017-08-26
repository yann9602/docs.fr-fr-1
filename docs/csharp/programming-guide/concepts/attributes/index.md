---
title: Attributs (C#)
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
ms.assetid: f148f13f-a0d5-4f22-9c87-4b73d5dde270
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
ms.openlocfilehash: ab55021a073f914905e29163ba2a669f69d6dcab
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="attributes-c"></a>Attributs (C#)
Les attributs fournissent une méthode puissante permettant d’associer des métadonnées ou des informations déclaratives avec du code (assemblys, types, méthodes, propriétés, etc.). Une fois associé à une entité de programme, l’attribut peut être interrogé à l’exécution à l’aide d’une technique appelée *réflexion*. Pour plus d’informations, consultez [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md).  
  
 Les attributs ont les propriétés suivantes :  
  
-   Les attributs ajoutent des métadonnées à un programme. Les *métadonnées* sont des informations sur les types définis dans un programme. Tous les assemblys .NET contiennent un ensemble spécifié de métadonnées qui décrivent les types et membres de types définis dans l’assembly. Vous pouvez ajouter des attributs personnalisés pour spécifier des informations supplémentaires si nécessaire. Pour plus d’informations, consultez [Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md).  
  
-   Vous pouvez appliquer un ou plusieurs attributs à des modules ou des assemblys entiers ou à de plus petits éléments de programmes, comme des classes et des propriétés.  
  
-   Les attributs peuvent accepter des arguments de la même façon que les méthodes et les propriétés.  
  
-   Votre programme peut examiner ses propres métadonnées ou celles d’autres programmes grâce à la réflexion. Pour plus d’informations, consultez [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md).  
  
## <a name="using-attributes"></a>Utilisation d'attributs  
 Les attributs peuvent être placés sur la quasi-totalité des déclarations, même si un attribut donné peut restreindre les types de déclarations sur lesquels il est valide. En C#, vous spécifiez un attribut en plaçant son nom, entouré de crochets ([]), au-dessus de la déclaration de l’entité à laquelle il s’applique.  
  
 Dans cet exemple, l’attribut <xref:System.SerializableAttribute> est utilisé pour appliquer une caractéristique spécifique à une classe :  
  
```csharp  
[System.Serializable]  
public class SampleClass  
{  
    // Objects of this type can be serialized.  
}  
```  
  
 Une méthode avec l’attribut <xref:System.Runtime.InteropServices.DllImportAttribute> est déclarée comme suit :  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
[System.Runtime.InteropServices.DllImport("user32.dll")]  
extern static void SampleMethod();  
```  
  
 Plusieurs attributs peuvent être placés dans une déclaration :  
  
```csharp  
using System.Runtime.InteropServices;  
```  
  
```csharp  
void MethodA([In][Out] ref double x) { }  
void MethodB([Out][In] ref double x) { }  
void MethodC([In, Out] ref double x) { }  
```  
  
 Certains attributs peuvent être spécifiés plusieurs fois pour une entité donnée. <xref:System.Diagnostics.ConditionalAttribute> est un exemple d’attribut à utilisation multiple :  
  
```csharp  
[Conditional("DEBUG"), Conditional("TEST1")]  
void TraceMethod()  
{  
    // ...  
}  
```  
  
> [!NOTE]
>  Par convention, tous les noms d’attributs se terminent par le mot « Attribute » pour les différencier d’autres éléments de .NET Framework. Toutefois, il est inutile de spécifier le suffixe d’attribut lorsque les attributs sont utilisés dans le code. Par exemple, `[DllImport]` équivaut à `[DllImportAttribute]`, mais `DllImportAttribute` est le nom réel de l’attribut dans .NET Framework.  
  
### <a name="attribute-parameters"></a>Paramètres d’attributs  
 Beaucoup d’attributs possèdent des paramètres. Ceux-ci peuvent être positionnels, sans nom ou nommés. Les paramètres positionnels doivent être spécifiés dans un certain ordre et ne peuvent pas être omis ; les paramètres nommés sont facultatifs et peuvent être spécifiés dans n’importe quel ordre. Les paramètres positionnels sont spécifiés en premier. Par exemple, ces trois attributs sont équivalents :  
  
```csharp  
[DllImport("user32.dll")]  
[DllImport("user32.dll", SetLastError=false, ExactSpelling=false)]  
[DllImport("user32.dll", ExactSpelling=false, SetLastError=false)]  
```  
  
 Le premier paramètre, le nom de la DLL, est positionnel et se place toujours en premier ; les autres sont nommés. Dans ce cas, les deux paramètres nommés ont la valeur false par défaut ; ainsi, ils peuvent être omis. Reportez-vous à la documentation de chaque attribut pour plus d’informations sur les valeurs des paramètres par défaut.  
  
### <a name="attribute-targets"></a>Cibles d'attribut  
 La *cible* d’un attribut est l’entité à laquelle s’applique l’attribut. Par exemple, un attribut peut s’appliquer à une classe, à une méthode particulière ou à un assembly entier. Par défaut, un attribut s’applique à l’élément qu’il précède. Mais vous pouvez également identifier de manière explicite, par exemple, si un attribut s’applique à une méthode, à son paramètre ou à sa valeur renvoyée.  
  
 Pour identifier de manière explicite une cible d’attribut, utilisez la syntaxe suivante :  
  
```csharp  
[target : attribute-list]  
```  
  
 La liste des valeurs `target` possibles est présentée dans le tableau suivant.  
  
|Valeur cible|S'applique à|  
|------------------|----------------|  
|`assembly`|Assembly entier|  
|`module`|Module d’assembly actuel|  
|`field`|Champ dans une classe ou un struct|  
|`event`|Événement|  
|`method`|Méthode ou accesseurs de propriété `get` et `set`|  
|`param`|Paramètres de méthode ou paramètres d’accesseur de propriété `set`|  
|`property`|Propriété|  
|`return`|Valeur de retour d’une méthode, indexeur de propriété ou accesseur de propriété `get`|  
|`type`|Struct, classe, interface, énumération ou délégué|  
  
 L’exemple suivant montre comment appliquer des attributs à des modules et assemblys. Pour plus d’informations, consultez [Attributs courants (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md).  
  
```csharp  
using System;  
using System.Reflection;  
[assembly: AssemblyTitleAttribute("Production assembly 4")]  
[module: CLSCompliant(true)]  
```  
  
 L’exemple suivant montre comment appliquer des attributs à des méthodes, des paramètres de méthode et des valeurs de retour de méthode en C#.  
  
```csharp  
// default: applies to method  
[SomeAttr]  
int Method1() { return 0; }  
  
// applies to method  
[method: SomeAttr]  
int Method2() { return 0; }  
  
// applies to return value  
[return: SomeAttr]  
int Method3() { return 0; }  
```  
  
> [!NOTE]
>  Quelle que soit la cible sur laquelle `SomeAttr` est défini comme étant valide, la cible `return` doit être spécifiée, même si `SomeAttr` a été défini pour s’appliquer seulement aux valeurs de retour. En d’autres termes, le compilateur n’utilise pas les informations `AttributeUsage` pour résoudre les cibles d’attribut ambiguës. Pour plus d’informations, consultez [AttributeUsage (C#)](../../../../csharp/programming-guide/concepts/attributes/attributeusage.md).  
  
## <a name="common-uses-for-attributes"></a>Utilisations courantes des attributs  
 La liste suivante comprend certaines des utilisations courantes des attributs dans le code :  
  
-   Marquer des méthodes avec l’attribut `WebMethod` dans les services web pour indiquer que la méthode doit pouvoir être appelée via le protocole SOAP. Pour plus d'informations, consultez <xref:System.Web.Services.WebMethodAttribute>.  
  
-   Décrire comment marshaler les paramètres de méthode en cas d’interaction avec du code natif. Pour plus d'informations, consultez <xref:System.Runtime.InteropServices.MarshalAsAttribute>.  
  
-   Décrire les propriétés COM des classes, méthodes et interfaces.  
  
-   Appeler du code non managé à l’aide de la classe <xref:System.Runtime.InteropServices.DllImportAttribute>.  
  
-   Décrire un assembly : titre, version, description ou marque.  
  
-   Décrire les membres d’une classe à sérialiser à des fins de persistance.  
  
-   Décrire le mappage entre les membres de classe et des nœuds XML à des fins de sérialisation XML.  
  
-   Décrire les exigences de sécurité des méthodes.  
  
-   Spécifier les caractéristiques employées pour appliquer la sécurité.  
  
-   Contrôler les optimisations par le compilateur juste-à-temps (JIT) pour que le code reste facile à déboguer.  
  
-   Obtenir des informations sur l’appelant d’une méthode.  
  
## <a name="related-sections"></a>Rubriques connexes  
 Pour plus d'informations, voir :  
  
-   [Création d’attributs personnalisés (C#)](../../../../csharp/programming-guide/concepts/attributes/creating-custom-attributes.md)  
  
-   [Accès à des attributs à l’aide de la réflexion (C#)](../../../../csharp/programming-guide/concepts/attributes/accessing-attributes-by-using-reflection.md)  
  
-   [Guide pratique pour créer une union C/C++ à l’aide d’attributs (C#)](../../../../csharp/programming-guide/concepts/attributes/how-to-create-a-c-cpp-union-by-using-attributes.md)  
  
-   [Attributs courants (C#)](../../../../csharp/programming-guide/concepts/attributes/common-attributes.md)  
  
-   [Informations relatives à l’appelant (C#)](../../../../csharp/programming-guide/concepts/caller-information.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de programmation C#](../../../../csharp/programming-guide/index.md)   
 [Réflexion (C#)](../../../../csharp/programming-guide/concepts/reflection.md)   
 [Attributs](https://msdn.microsoft.com/library/5x6cd29c)


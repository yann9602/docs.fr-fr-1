---
title: "Acc&#232;s aux attributs personnalis&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "attributs (.NET Framework), accéder"
  - "attributs personnalisés, accessibilité"
  - "réflexion, attributs personnalisés"
ms.assetid: 1d8e3398-00d8-47d5-a084-214f9859d3d7
caps.latest.revision: 15
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 14
---
# Acc&#232;s aux attributs personnalis&#233;s
Une fois les attributs associés aux éléments du programme, il est possible d'utiliser la réflexion pour exécuter des requêtes visant à déterminer leur existence et leurs valeurs.  Dans la version 1.0 et 1.1 du .NET Framework, les attributs personnalisés sont examinés dans le contexte d'exécution.  Le .NET Framework version 2.0 fournit un nouveau contexte de chargement, le contexte de réflexion uniquement, lequel permet d'examiner du code qui ne peut pas être chargé pour exécution.  
  
## Contexte de réflexion uniquement  
 Le code chargé dans le contexte de réflexion uniquement ne peut pas être exécuté.  Cela signifie qu'il est impossible de créer des instances d'attributs personnalisés car cela nécessiterait l'exécution de leurs constructeurs.  Pour charger et examiner des attributs personnalisés dans le contexte de réflexion uniquement, utilisez la classe <xref:System.Reflection.CustomAttributeData>.  Vous pouvez obtenir des instances de cette classe en utilisant la surcharge appropriée de la méthode statique <xref:System.Reflection.CustomAttributeData.GetCustomAttributes%2A?displayProperty=fullName>.  Consultez [Comment : charger des assemblys dans le contexte de réflexion uniquement](../../../docs/framework/reflection-and-codedom/how-to-load-assemblies-into-the-reflection-only-context.md).  
  
## Contexte d'exécution  
 Les principales méthodes de réflexion utilisées pour l'exécution de requêtes se rapportant aux attributs dans le contexte d'exécution figurent dans <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName> et <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>.  
  
 L'accessibilité d'un attribut personnalisé est vérifiée par rapport à l'assembly auquel il est attaché.  Cela équivaut à vérifier si une méthode d'un type de l'assembly auquel est attaché l'attribut personnalisé peut appeler le constructeur de cet attribut.  
  
 Les méthodes telles que <xref:System.Reflection.Assembly.GetCustomAttributes%28System.Boolean%29?displayProperty=fullName> vérifient la visibilité et l'accessibilité de l'argument de type.  Seul le code de l'assembly qui contient le type défini par l'utilisateur peut récupérer un attribut personnalisé de ce type à l'aide de **GetCustomAttributes**.  
  
 L'exemple C\# suivant est un modèle de design d'attributs personnalisés courant.  Il illustre le modèle de réflexion d'attribut personnalisé du runtime.  
  
```  
System.DLL  
public class DescriptionAttribute : Attribute  
{  
}  
  
System.Web.DLL  
internal class MyDescriptionAttribute : DescriptionAttribute  
{  
}  
  
public class LocalizationExtenderProvider  
{  
    [MyDescriptionAttribute(...)]  
    public CultureInfo GetLanguage(...)  
    {  
    }  
}  
```  
  
 Si le runtime tente de récupérer les attributs personnalisés du type d'attribut personnalisé public <xref:System.ComponentModel.DescriptionAttribute> attaché à la méthode **GetLanguage**, il effectue les actions suivantes :  
  
1.  Vérifier que l'argument de type **DescriptionAttribute** pour **Type.GetCustomAttributes**\(Type *type*\) est public, et qu'il est, par conséquent, visible et accessible.  
  
2.  Vérifier que le type défini par l'utilisateur **MyDescriptionAttribute**, dérivé de **DescriptionAttribute**, est visible et accessible dans l'assembly **System.Web.DLL**, où il est attaché à la méthode **GetLanguage**\(\).  
  
3.  Vérifier que le constructeur de **MyDescriptionAttribute** est visible et accessible dans l'assembly **System.Web.DLL**.  
  
4.  Appeler le constructeur de **MyDescriptionAttribute** à l'aide des paramètres d'attribut personnalisé et retourner le nouvel objet à l'appelant.  
  
 Le modèle de réflexion d'attribut personnalisé peut diffuser des instances de types définis par l'utilisateur hors de l'assembly dans lequel le type est défini.  Cela n'est guère différent des membres de la bibliothèque système du runtime qui retournent des instances de types définis par l'utilisateur, par exemple [Type.GetMethods\(\)](frlrfSystemTypeClassGetMethodsTopic) qui retourne un tableau d'objets **RuntimeMethodInfo**.  Pour empêcher un client de découvrir des informations se rapportant à un type d'attribut personnalisé défini par l'utilisateur, faites des membres du type des membres non publics.  
  
 L'exemple suivant montre la procédure de base pour utiliser la réflexion et accéder aux attributs personnalisés.  
  
 [!code-cpp[CustomAttributeData#2](../../../samples/snippets/cpp/VS_Snippets_CLR/CustomAttributeData/CPP/source2.cpp#2)]
 [!code-csharp[CustomAttributeData#2](../../../samples/snippets/csharp/VS_Snippets_CLR/CustomAttributeData/CS/source2.cs#2)]
 [!code-vb[CustomAttributeData#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/CustomAttributeData/VB/source2.vb#2)]  
  
## Voir aussi  
 <xref:System.Reflection.MemberInfo.GetCustomAttributes%2A?displayProperty=fullName>   
 <xref:System.Attribute.GetCustomAttributes%2A?displayProperty=fullName>   
 [Affichage des informations de type](../../../docs/framework/reflection-and-codedom/viewing-type-information.md)   
 [Considérations sur la sécurité de la réflexion](../../../docs/framework/reflection-and-codedom/security-considerations-for-reflection.md)
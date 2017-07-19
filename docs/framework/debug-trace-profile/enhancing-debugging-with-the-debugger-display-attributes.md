---
title: "Enhancing Debugging with the Debugger Display Attributes | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "debugger, display attributes"
  - "DebuggerTypeProxyAttribute attribute"
  - "debugging [.NET Framework], debugger display attributes"
  - "DebuggerDisplayAttribute attribute"
  - "display attributes for debugger"
  - "DebuggerBrowsableAttribute attribute"
ms.assetid: 72bb7aa9-459b-42c4-9163-9312fab4c410
caps.latest.revision: 7
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 7
---
# Enhancing Debugging with the Debugger Display Attributes
Les attributs d'affichage de débogueur permettent au développeur du type, qui spécifie et appréhende le mieux le comportement d'exécution de ce type, de spécifier également ce à quoi le type ressemblera une fois affiché dans un débogueur.  De plus, les attributs d'affichage de débogueur qui fournissent une propriété `Target` peuvent être appliqués au niveau de l'assembly par des utilisateurs sans qu'il leur soit nécessaire de connaître le code source.  L'attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> contrôle la façon dont un type ou un membre s'affiche dans les fenêtres de variables du débogueur.  L'attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> contrôle si une classe ou un champ s'affiche dans les fenêtres de variables du débogueur et comment ils s'affichent.  L'attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> spécifie un type de substitution, ou un proxy, d'un type et modifie le mode d'affichage de ce type dans les fenêtres de débogage.  Lorsque vous visualisez une variable possédant un proxy, ou un type de substitution, ce dernier remplace le type d'origine dans la fenêtre d'affichage du débogage. La fenêtre de variables du débogueur  n'affiche que les membres publics du type du proxy.  Les membres privés ne sont pas affichés.  
  
## Utilisation de DebuggerDisplayAttribute  
 Le constructeur <xref:System.Diagnostics.DebuggerDisplayAttribute.%23ctor%2A> possède un argument unique : une chaîne à afficher dans la colonne valeur pour les instances du type.  Cette chaîne peut contenir des accolades \({ et }\).  Le texte entre accolades est évalué comme une expression.  Par exemple, le code C\# suivant entraîne l'affichage de "Count \= 4" lorsque le signe plus \(\+\) est sélectionné pour développer l'affichage de débogueur pour une instance de `MyHashtable`.  
  
```  
[DebuggerDisplay("Count = {count}")]  
class MyHashtable  
{  
    public int count = 4;  
}  
```  
  
 Les attributs appliqués aux propriétés référencées dans l'expression ne sont pas traités.  Pour le compilateur C\#, une expression générale est autorisée si elle ne possède qu'un accès implicite à cette référence pour l'instance actuelle du type cible.  L'expression est limitée ; il n'existe aucun accès aux alias, aux variables locales ou aux pointeurs.  En code C\#, vous pouvez utiliser une expression générale entre accolades qui dispose d'un accès implicite au pointeur `this` uniquement pour l'instance actuelle du type cible.  
  
 Si, par exemple, un objet C\# a un `ToString()` substitué, le débogueur appellera la substitution et affichera son résultat au lieu du `{<typeName>}.` standard. Si vous avez substitué `ToString()`, vous ne devez donc pas utiliser <xref:System.Diagnostics.DebuggerDisplayAttribute>.  Si vous utilisez les deux, l'attribut <xref:System.Diagnostics.DebuggerDisplayAttribute> prend la priorité sur la substitution de `ToString()`.  
  
## Utilisation de DebuggerBrowsableAttribute  
 Appliquez l'attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute> à un champ ou une propriété pour spécifier la façon dont le champ ou la propriété doit être affiché dans la fenêtre du débogueur.  Le constructeur pour cet attribut accepte l'une des valeurs d'énumération <xref:System.Diagnostics.DebuggerBrowsableState> qui spécifient l'un des états suivants :  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> indique que le membre n'est pas affiché dans la fenêtre de données.  Par exemple, l'utilisation de cette valeur pour <xref:System.Diagnostics.DebuggerBrowsableAttribute> sur un champ supprime le champ de la hiérarchie ; le champ n'est pas affiché lorsque vous développez le type englobant en cliquant sur le signe plus \(\+\) pour l'instance de type.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> indique que le membre est affiché mais n'est pas développé par défaut.  Il s'agit du comportement par défaut.  
  
-   <xref:System.Diagnostics.DebuggerBrowsableState> indique que le membre lui\-même n'est pas affiché, mais ses objets constituants sont affichés s'il s'agit d'un tableau ou d'une collection.  
  
> [!NOTE]
>  <xref:System.Diagnostics.DebuggerBrowsableAttribute> n'est pas pris en charge dans la version 2.0 du .NET Framework.  
  
 L'exemple de code suivant illustre l'utilisation du <xref:System.Diagnostics.DebuggerBrowsableAttribute> pour empêcher la propriété qui le suit d'apparaître dans la fenêtre de débogage pour la classe.  
  
```  
[DebuggerBrowsable(DebuggerBrowsableState.Never)]  
public static string y = "Test String";  
```  
  
## Utilisation de DebuggerTypeProxy  
 Utilisez l'attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> lorsque vous avez besoin de modifier radicalement l'affichage de débogage d'un type, sans toutefois modifier le type lui\-même.  L'attribut <xref:System.Diagnostics.DebuggerTypeProxyAttribute> est utilisé pour spécifier un proxy d'affichage pour un type, ce qui permet à un développeur d'adapter l'affichage pour le type.  Cet attribut, à l'instar de <xref:System.Diagnostics.DebuggerDisplayAttribute>, peut être utilisé également au niveau de l'assembly, auquel cas la propriété <xref:System.Diagnostics.DebuggerTypeProxyAttribute.Target%2A> spécifie le type pour lequel le proxy sera utilisé.  Il est généralement recommandé que cet attribut spécifie un type imbriqué privé qui se produit dans le type auquel l'attribut est appliqué.  Évaluateur d'expression qui prend en charge des contrôles de visionneuses de type pour cet attribut lors de l'affichage d'un type.  Si l'attribut est trouvé, l'évaluateur d'expression substitue le type du proxy d'affichage au type auquel l'attribut est appliqué.  
  
 Lorsque <xref:System.Diagnostics.DebuggerTypeProxyAttribute> est présent, la fenêtre des variables du débogueur affiche uniquement les membres publics du type de proxy.  Les membres privés ne sont pas affichés.  Le comportement de la fenêtre de données n'est pas modifié par les affichages améliorés par les attributs.  
  
 Pour éviter une dégradation inutile des performances, les attributs du proxy d'affichage ne sont pas traités tant que l'objet n'est pas développé, soit par un clic de l'utilisateur sur le signe plus \(\+\) en regard du type dans une fenêtre de données, soit via l'application de l'attribut <xref:System.Diagnostics.DebuggerBrowsableAttribute>.  Par conséquent, il est recommandé de n'appliquer aucun attribut au type d'affichage.  Les attributs peuvent et doivent être appliqués dans le corps du type d'affichage.  
  
 L'exemple de code suivant montre comment utiliser <xref:System.Diagnostics.DebuggerTypeProxyAttribute> pour spécifier un type à utiliser en tant que proxy de l'affichage du débogueur.  
  
```  
  
[DebuggerTypeProxy(typeof(HashtableDebugView))]  
class MyHashtable : Hashtable  
{  
    private const string TestString =   
        "This should not appear in the debug window.";  
  
    internal class HashtableDebugView  
    {  
        private Hashtable hashtable;  
        public const string TestStringProxy =   
            "This should appear in the debug window.";  
  
        // The constructor for the type proxy class must have a   
        // constructor that takes the target type as a parameter.  
        public HashtableDebugView(Hashtable hashtable)  
        {  
            this.hashtable = hashtable;  
        }  
    }  
}  
```  
  
## Exemple  
  
### Description  
 L'exemple de code suivant peut être affiché dans [!INCLUDE[vsprvslong](../../../includes/vsprvslong-md.md)] pour consulter les résultats de l'application des attributs <xref:System.Diagnostics.DebuggerDisplayAttribute>, <xref:System.Diagnostics.DebuggerBrowsableAttribute> et <xref:System.Diagnostics.DebuggerTypeProxyAttribute>.  
  
### Code  
 [!code-cpp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/cpp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/cpp/program.cpp#1)]
 [!code-csharp[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/csharp/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/CS/program.cs#1)]
 [!code-vb[System.Diagnostics.DebuggerBrowsableAttribute#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR_System/system.Diagnostics.DebuggerBrowsableAttribute/VB/module1.vb#1)]  
  
## Voir aussi  
 <xref:System.Diagnostics.DebuggerDisplayAttribute>   
 <xref:System.Diagnostics.DebuggerBrowsableAttribute>   
 <xref:System.Diagnostics.DebuggerTypeProxyAttribute>
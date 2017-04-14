---
title: "Hi&#233;rarchie des exceptions | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "exceptions, types"
  - "exécution, exceptions"
  - "exceptions de base"
  - "ApplicationException (classe)"
  - "exceptions Common language runtime"
  - "Exceptions COM interop,"
  - "exceptions, hiérarchies"
ms.assetid: f7d68675-be06-40fb-a555-05f0c5a6f66b
caps.latest.revision: 14
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 14
---
# Hi&#233;rarchie des exceptions
Il existe deux types d’exceptions : les exceptions générées par un programme en cours d’exécution et les exceptions générées par le Common Language Runtime. De plus, il existe une hiérarchie des exceptions pouvant être levées soit par une application soit par le runtime.  
  
 Le <xref:System.Exception?displayProperty=fullName> classe est la classe de base pour les exceptions. Plusieurs classes d’exceptions héritent directement de <xref:System.Exception>, y compris <xref:System.ApplicationException> et <xref:System.SystemException>. Ces deux classes servent de base à presque toutes les exceptions runtime.  
  
 La plupart des exceptions qui dérivent directement de <xref:System.Exception> ajouter aucune fonctionnalité et aucun membre. Par exemple, le <xref:System.InvalidCastException> hiérarchie de classe est la suivante :  
  
 <xref:System.Object> <xref:System.Exception> <xref:System.SystemException> <xref:System.InvalidCastException>  
  
 Le runtime lève la classe dérivée appropriée de <xref:System.SystemException> lorsque des erreurs se produisent. Ces erreurs se produisent lors de l’échec de vérifications à l’exécution (par exemple, lors de la détection d’un tableau hors limites), et peuvent se produire pendant l’exécution de n’importe quelle méthode. Si vous concevez une application qui crée de nouvelles exceptions, vous devez dériver ces exceptions de la <xref:System.Exception> classe. Il est déconseillé d’intercepter un <xref:System.SystemException>, ni de bonnes pratiques de programmation pour lever une <xref:System.SystemException> dans votre application.  
  
 Les exceptions les plus graves, celles levées par le runtime ou dans des conditions, inclure <xref:System.ExecutionEngineException>, <xref:System.StackOverflowException>, et <xref:System.OutOfMemoryException>.  
  
 Les exceptions d’interopérabilité dérivent <xref:System.SystemException> et sont encore étendues par <xref:System.Runtime.InteropServices.ExternalException>. Par exemple, <xref:System.Runtime.InteropServices.COMException> est l’exception levée pendant les opérations COM interop et dérive <xref:System.Runtime.InteropServices.ExternalException>. <xref:System.ComponentModel.Win32Exception> et <xref:System.Runtime.InteropServices.SEHException> également dériver de <xref:System.Runtime.InteropServices.ExternalException>.  
  
## <a name="hierarchy-of-runtime-exceptions"></a>Hiérarchie des exceptions runtime  
 Le runtime possède un jeu de base d’exceptions dérivant de <xref:System.SystemException> qu’il lève lorsqu’il exécute des instructions individuelles. Le tableau suivant répertorie de manière hiérarchique les exceptions standard fournies par le runtime et les conditions dans lesquelles vous devez créer une classe dérivée.  
  
|Type d'exception|Type de base|Description|Exemple|  
|--------------------|---------------|-----------------|-------------|  
|[Exception](../../../docs/standard/exceptions/exception-class-and-properties.md)|<xref:System.Object>|Classe de base pour toutes les exceptions.|Aucun (utilisez une classe dérivée de cette exception).|  
|<xref:System.SystemException>|<xref:System.Exception>|Classe de base pour toutes les erreurs générées par le runtime.|Aucun (utilisez une classe dérivée de cette exception).|  
|<xref:System.IndexOutOfRangeException>|<xref:System.SystemException>|Levée par le runtime uniquement en cas d’indexation incorrecte du tableau.|Indexation d’un tableau en dehors de sa plage valide :<br /><br /> `var i = arr[arr.Length + 1];`<br /><br /> `Dim i = arr(arr.Length + 1)`|  
|<xref:System.NullReferenceException>|<xref:System.SystemException>|Levée par le runtime uniquement si un objet Null est référencé.|`object o = null; string s = o.ToString();`<br /><br /> `Dim o As Object = Nothing Dim s As String = o.ToString()`|  
|<xref:System.AccessViolationException>|<xref:System.SystemException>|Levée par le runtime uniquement lors d’un accès à une mémoire non valide.|Se produit lors de l’interaction avec du code non managé ou du code managé unsafe, si un pointeur non valide est utilisé.|  
|<xref:System.InvalidOperationException>|<xref:System.SystemException>|Levée par les méthodes en cas d’état non valide.|L’énumérateur de l’appel `GetNext` méthode après la suppression d’un élément de la collection sous-jacente.|  
|<xref:System.ArgumentException>|<xref:System.SystemException>|Classe de base pour toutes les exceptions d’argument.|Aucun (utilisez une classe dérivée de cette exception).|  
|<xref:System.ArgumentNullException>|<xref:System.ArgumentException>|Levée par les méthodes qui n’acceptent pas la valeur Null pour un argument.|`String s = null; int i = "Calculate".IndexOf(s);`<br /><br /> `Dim s As String = Nothing Dim i As Integer = "Calculate".IndexOf(s)`|  
|<xref:System.ArgumentOutOfRangeException>|<xref:System.ArgumentException>|Levée par les méthodes qui vérifient que les arguments sont inclus dans une plage donnée.|`String s = "string"; s = s.Substring(s.Length + 1);`<br /><br /> `Dim s As String = "string" s = s.Substring(s.Length + 1)`|  
|<xref:System.Runtime.InteropServices.ExternalException>|<xref:System.SystemException>|Classe de base de toutes les exceptions qui se produisent ou qui sont destinées à des environnements à l’extérieur du runtime.|Aucun (utilisez une classe dérivée de cette exception).|  
|<xref:System.Runtime.InteropServices.COMException>|<xref:System.Runtime.InteropServices.ExternalException>|Exception qui encapsule les informations HRESULT COM.|Utilisé dans COM Interop.|  
|<xref:System.Runtime.InteropServices.SEHException>|<xref:System.Runtime.InteropServices.ExternalException>|Exception encapsulant les informations de la gestion structurée des exceptions sur Win32.|Utilisé dans l’interopérabilité du code non managé.|  
  
## <a name="see-also"></a>Voir aussi  
 [Classe exception et propriétés](../../../docs/standard/exceptions/exception-class-and-properties.md)   
 [Notions de base de la gestion des exceptions](../../../docs/standard/exceptions/exception-handling-fundamentals.md)   
 [Meilleures pratiques pour les Exceptions](../../../docs/standard/exceptions/best-practices-for-exceptions.md)   
 [Exceptions](../../../docs/standard/exceptions/index.md)
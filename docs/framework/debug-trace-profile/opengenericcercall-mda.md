---
title: "openGenericCERCall MDA | Microsoft Docs"
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
  - "MDAs (managed debugging assistants), CER calls"
  - "open generic CER calls"
  - "constrained execution regions"
  - "openGenericCERCall MDA"
  - "CER calls"
  - "managed debugging assistants (MDAs), CER calls"
  - "generics [.NET Framework], open generic CER calls"
ms.assetid: da3e4ff3-2e67-4668-9720-fa776c97407e
caps.latest.revision: 13
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 13
---
# openGenericCERCall MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `openGenericCERCall` est activé pour signaler qu'un graphique d'une région d'exécution limitée avec des variables de type générique au niveau de la méthode racine est traité au moment de la compilation JIT ou au moment de la génération d'images natives et qu'au moins une des variables de type générique est un type référence d'objet.  
  
## Symptômes  
 Le code de la région d'exécution limitée ne s'exécute pas lorsqu'un thread est interrompu ou qu'un domaine d'application est déchargé.  
  
## Cause  
 Au moment de la compilation JIT, une instanciation contenant un type référence d'objet est uniquement représentative car le code obtenu est partagé et chacune des variables de type référence d'objet peut représenter n'importe quel type référence d'objet.  Cela peut empêcher la préparation préalable de certaines ressources d'exécution.  
  
 En particulier, les méthodes comportant des variables de type générique peuvent allouer des ressources en différé en arrière\-plan.  Celles\-ci sont désignées par le terme « entrées de dictionnaire générique ».  Par exemple, pour l'instruction `List<T> list = new List<T>();`  où `T` est une variable de type générique que le runtime doit rechercher et dont il doit éventuellement créer l'instanciation exacte au moment de l'exécution, par exemple `List<Object>, List<String>` `` , etc.  L'opération peut échouer pour diverses raisons qui échappent au contrôle du développeur, par exemple une insuffisance de mémoire.  
  
 Cet Assistant Débogage managé doit être activé uniquement au moment de la compilation JIT et non au moment d'une instanciation exacte.  
  
 Lorsque cet Assistant Débogage managé est activé, les symptômes probables sont un dysfonctionnement des régions d'exécution limitée pour les instanciations incorrectes.  En fait, le runtime ne tente pas d'implémenter une région d'exécution limitée dans des circonstances ayant provoqué l'activation de l'Assistant Débogage managé.  Dès lors, si le développeur utilise une instanciation partagée de la région d'exécution limitée, les erreurs de compilation JIT, les erreurs de chargement de types génériques ou les abandons de threads dans la région d'exécution limitée prévue ne sont pas interceptés.  
  
## Résolution  
 N'utilisez pas de variables de type générique qui sont des types référence d'objet pour les méthodes susceptibles de contenir une région d'exécution limitée.  
  
## Effet sur le runtime  
 Ce MDA n'a aucun effet sur le CLR.  
  
## Sortie  
 Le message suivant constitue un exemple de sortie de cet Assistant Débogage managé.  
  
 `Method 'GenericMethodWithCer', which contains at least one constrained execution region, cannot be prepared automatically since it has one or more unbound generic type parameters.`  
  
 `The caller must ensure this method is prepared explicitly at run time prior to execution.`  
  
 `method name="GenericMethodWithCer"`  
  
 `declaringType name="OpenGenericCERCall"`  
  
## Configuration  
  
```  
<mdaConfig>  
  <assistants>  
    <openGenericCERCall/>  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 Le code de la région d'exécution limitée n'est pas exécuté.  
  
```  
using System;  
using System.Collections.Generic;  
using System.Runtime.CompilerServices;  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        CallGenericMethods();  
    }  
    static void CallGenericMethods()  
    {  
        // This call is correct. The instantiation of the method  
        // contains only nonreference types.  
        MyClass.GenericMethodWithCer<int>();  
  
        // This call is incorrect. A shared version of the method that  
        // cannot be completely analyzed will be JIT-compiled. The   
        // MDA will be activated at JIT-compile time, not at run time.  
        MyClass.GenericMethodWithCer<String>();  
    }  
}  
  
    class MyClass  
{  
    public static void GenericMethodWithCer<T>()  
    {  
        RuntimeHelpers.PrepareConstrainedRegions();  
        try  
        {  
  
        }  
        finally  
        {  
            // This is the start of the CER.  
            Console.WriteLine("In finally block.");  
        }  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.CompilerServices.RuntimeHelpers.PrepareMethod%2A>   
 <xref:System.Runtime.ConstrainedExecution>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
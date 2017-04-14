---
title: "jitCompilationStart MDA | Microsoft Docs"
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
  - "JIT compilation"
  - "MDAs (managed debugging assistants), JIT compilation"
  - "JitCompilationStart MDA"
  - "managed debugging assistants (MDAs), JIT compilation"
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: 11
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 11
---
# jitCompilationStart MDA
L'Assistant Débogage managé \(MDA, Managed Debugging Assistant\) `jitCompilationStart` est activé pour signaler le moment où le compilateur juste\-à\-temps \(JIT, Just\-In\-Time\) commence à compiler une fonction.  
  
## Symptômes  
 La taille du jeu de travail augmente pour un programme qui est déjà au format d'image natif car mscorjit.dll est chargé dans le processus.  
  
## Cause  
 Les assemblys dont dépend le programme n'ont pas tous été générés au format natif, ou ceux qui l'ont été ne sont pas correctement inscrits.  
  
## Résolution  
 L'activation de ce MDA vous permet de déterminer la fonction qui est compilée juste\-à\-temps \(JIT\).  Déterminez si l'assembly qui contient la fonction est généré au format natif et s'il est correctement inscrit.  
  
## Effet sur le runtime  
 Ce MDA enregistre un message juste avant qu'une méthode soit compilée juste\-à\-temps, de sorte que l'activation de ce MDA a un impact significatif sur les performances.  Notez que si une méthode est inline, ce MDA ne générera pas de message séparé.  
  
## Sortie  
 L'exemple de code suivant affiche la sortie de l'exemple.  Dans ce cas, la sortie montre que, dans l'assembly Test, la méthode "m" sur la classe "ns2.CO" a été compilée juste\-à\-temps \(JIT\).  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## Configuration  
 Le fichier de configuration suivant présente divers filtres qui peuvent être utilisés pour filtrer les méthodes signalées lorsqu'elles sont d'abord compilées juste\-à\-temps \(JIT\).  Vous pouvez spécifier que toutes les méthodes soient signalées en affectant \* à la valeur de l'attribut name.  
  
```  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## Exemple  
 L'exemple de code suivant doit normalement être utilisé avec le fichier de configuration précédent.  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## Voir aussi  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>   
 [Diagnosing Errors with Managed Debugging Assistants](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)   
 [Interop Marshaling](../../../docs/framework/interop/interop-marshaling.md)
---
title: "Paramètres et valeurs de retour pour les procédures multithread (C#)"
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
ms.assetid: ba63c30c-d9f0-4962-b5c7-9d83ba851e6a
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
ms.openlocfilehash: 5e377a006409dbae49b3c00297f69e8d55a01295
ms.contentlocale: fr-fr
ms.lasthandoff: 07/28/2017

---
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a>Paramètres et valeurs de retour pour les procédures multithread (C#)
Fournir des paramètres et retourner des valeurs dans une application multithread est complexe, car le constructeur de la classe thread doit recevoir une référence à une procédure qui n’accepte aucun argument et ne retourne aucune valeur. Les sections suivantes présentent plusieurs moyens simples pour fournir des paramètres et retourner des valeurs à partir de procédures exécutées sur des threads distincts.  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a>Fournir des paramètres pour des procédures multithread  
 Le meilleur moyen de fournir des paramètres pour un appel de méthode multithread consiste à inclure la méthode cible dans une classe et à définir les champs de cette classe à utiliser comme paramètres pour le nouveau thread. Cette approche présente l’avantage de vous permettre de créer une autre instance de la classe, avec ses propres paramètres, chaque fois que vous souhaitez démarrer un nouveau thread. Prenons l’exemple d’une fonction calculant la surface d’un triangle, comme dans le code suivant :  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 Vous pouvez écrire une classe qui inclut la fonction `CalcArea` et crée des champs pour stocker les paramètres d’entrée, comme suit :  
  
```csharp  
class AreaClass  
{  
    public double Base;  
    public double Height;  
    public double Area;  
    public void CalcArea()  
    {  
        Area = 0.5 * Base * Height;  
        MessageBox.Show("The area is: " + Area.ToString());  
    }  
}  
```  
  
 Pour utiliser `AreaClass`, vous créez un objet `AreaClass`, puis vous définissez les propriétés `Base` et `Height` comme indiqué dans le code suivant :  
  
```csharp  
protected void TestArea()  
{  
    AreaClass AreaObject = new AreaClass();  
  
    System.Threading.Thread Thread =  
        new System.Threading.Thread(AreaObject.CalcArea);  
    AreaObject.Base = 30;  
    AreaObject.Height = 40;  
    Thread.Start();  
}  
```  
  
 Notez que la procédure `TestArea` ne vérifie pas la valeur du champ `Area` après avoir appelé la méthode `CalcArea`. Étant donné que `CalcArea` s’exécute sur un thread distinct, le champ `Area` risque de ne pas être défini si vous le vérifiez immédiatement après avoir appelé `Thread.Start`. La section suivante présente une méthode plus appropriée pour retourner des valeurs à partir de procédures multithread.  
  
## <a name="returning-values-from-multithreaded-procedures"></a>Retourner des valeurs à partir de procédures multithread  
 Retourner des valeurs à partir de procédures exécutées sur des threads distincts est compliqué du fait que les procédures ne peuvent pas être des fonctions, ni utiliser d’arguments `ByRef`. Le moyen le plus simple de retourner des valeurs consiste à utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour gérer vos threads et déclencher un événement à la fin de la tâche, puis traiter les résultats à l’aide d’un gestionnaire d’événements.  
  
 L’exemple suivant retourne une valeur en déclenchant un événement à partir d’une procédure exécutée sur un thread distinct :  
  
```csharp  
class AreaClass2  
{  
    public double Base;  
    public double Height;  
    public double CalcArea()  
    {  
        // Calculate the area of a triangle.  
        return 0.5 * Base * Height;  
    }  
}  
  
private System.ComponentModel.BackgroundWorker BackgroundWorker1  
    = new System.ComponentModel.BackgroundWorker();  
  
private void TestArea2()  
{  
    InitializeBackgroundWorker();  
  
    AreaClass2 AreaObject2 = new AreaClass2();  
    AreaObject2.Base = 30;  
    AreaObject2.Height = 40;  
  
    // Start the asynchronous operation.  
    BackgroundWorker1.RunWorkerAsync(AreaObject2);  
}  
  
private void InitializeBackgroundWorker()  
{  
    // Attach event handlers to the BackgroundWorker object.  
    BackgroundWorker1.DoWork +=  
        new System.ComponentModel.DoWorkEventHandler(BackgroundWorker1_DoWork);  
    BackgroundWorker1.RunWorkerCompleted +=  
        new System.ComponentModel.RunWorkerCompletedEventHandler(BackgroundWorker1_RunWorkerCompleted);  
}  
  
private void BackgroundWorker1_DoWork(  
    object sender,  
    System.ComponentModel.DoWorkEventArgs e)  
{  
    AreaClass2 AreaObject2 = (AreaClass2)e.Argument;  
    // Return the value through the Result property.  
    e.Result = AreaObject2.CalcArea();  
}  
  
private void BackgroundWorker1_RunWorkerCompleted(  
    object sender,  
    System.ComponentModel.RunWorkerCompletedEventArgs e)  
{  
    // Access the result through the Result property.  
    double Area = (double)e.Result;  
    MessageBox.Show("The area is: " + Area.ToString());  
}  
```  
  
 Vous pouvez fournir des paramètres et retourner des valeurs aux threads de Thread Pool en utilisant la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>. Les threads de Timer Thread prennent également en charge un objet d’état à cet effet. Pour plus d’informations sur la mise en pool de threads et les composants Timer Thread, consultez [Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) et [Composants Timer Thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md)   
 [Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md)   
 [Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md)   
 [Événements](../../../../csharp/programming-guide/events/index.md)   
 [Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md)   
 [Délégués](../../../../csharp/programming-guide/delegates/index.md)   
 [Multithreading dans les composants](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)


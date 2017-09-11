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
# <a name="parameters-and-return-values-for-multithreaded-procedures-c"></a><span data-ttu-id="3f7b3-102">Paramètres et valeurs de retour pour les procédures multithread (C#)</span><span class="sxs-lookup"><span data-stu-id="3f7b3-102">Parameters and Return Values for Multithreaded Procedures (C#)</span></span>
<span data-ttu-id="3f7b3-103">Fournir des paramètres et retourner des valeurs dans une application multithread est complexe, car le constructeur de la classe thread doit recevoir une référence à une procédure qui n’accepte aucun argument et ne retourne aucune valeur.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-103">Supplying and returning values in a multithreaded application is complicated because the constructor for the thread class must be passed a reference to a procedure that takes no arguments and returns no value.</span></span> <span data-ttu-id="3f7b3-104">Les sections suivantes présentent plusieurs moyens simples pour fournir des paramètres et retourner des valeurs à partir de procédures exécutées sur des threads distincts.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-104">The following sections show some simple ways to supply parameters and return values from procedures on separate threads.</span></span>  
  
## <a name="supplying-parameters-for-multithreaded-procedures"></a><span data-ttu-id="3f7b3-105">Fournir des paramètres pour des procédures multithread</span><span class="sxs-lookup"><span data-stu-id="3f7b3-105">Supplying Parameters for Multithreaded Procedures</span></span>  
 <span data-ttu-id="3f7b3-106">Le meilleur moyen de fournir des paramètres pour un appel de méthode multithread consiste à inclure la méthode cible dans une classe et à définir les champs de cette classe à utiliser comme paramètres pour le nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-106">The best way to supply parameters for a multithreaded method call is to wrap the target method in a class and define fields for that class that will serve as parameters for the new thread.</span></span> <span data-ttu-id="3f7b3-107">Cette approche présente l’avantage de vous permettre de créer une autre instance de la classe, avec ses propres paramètres, chaque fois que vous souhaitez démarrer un nouveau thread.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-107">The advantage of this approach is that you can create a new instance of the class, with its own parameters, every time you want to start a new thread.</span></span> <span data-ttu-id="3f7b3-108">Prenons l’exemple d’une fonction calculant la surface d’un triangle, comme dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3f7b3-108">For example, suppose you have a function that calculates the area of a triangle, as in the following code:</span></span>  
  
```csharp  
double CalcArea(double Base, double Height)  
{  
    return 0.5 * Base * Height;  
}  
```  
  
 <span data-ttu-id="3f7b3-109">Vous pouvez écrire une classe qui inclut la fonction `CalcArea` et crée des champs pour stocker les paramètres d’entrée, comme suit :</span><span class="sxs-lookup"><span data-stu-id="3f7b3-109">You can write a class that wraps the `CalcArea` function and creates fields to store input parameters, as follows:</span></span>  
  
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
  
 <span data-ttu-id="3f7b3-110">Pour utiliser `AreaClass`, vous créez un objet `AreaClass`, puis vous définissez les propriétés `Base` et `Height` comme indiqué dans le code suivant :</span><span class="sxs-lookup"><span data-stu-id="3f7b3-110">To use the `AreaClass`, you can create an `AreaClass` object, and set the `Base` and `Height` properties as shown in the following code:</span></span>  
  
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
  
 <span data-ttu-id="3f7b3-111">Notez que la procédure `TestArea` ne vérifie pas la valeur du champ `Area` après avoir appelé la méthode `CalcArea`.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-111">Notice that the `TestArea` procedure does not check the value of the `Area` field after calling the `CalcArea` method.</span></span> <span data-ttu-id="3f7b3-112">Étant donné que `CalcArea` s’exécute sur un thread distinct, le champ `Area` risque de ne pas être défini si vous le vérifiez immédiatement après avoir appelé `Thread.Start`.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-112">Because `CalcArea` runs on a separate thread, the `Area` field is not guaranteed to be set if you check it immediately after calling `Thread.Start`.</span></span> <span data-ttu-id="3f7b3-113">La section suivante présente une méthode plus appropriée pour retourner des valeurs à partir de procédures multithread.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-113">The next section discusses a better way to return values from multithreaded procedures.</span></span>  
  
## <a name="returning-values-from-multithreaded-procedures"></a><span data-ttu-id="3f7b3-114">Retourner des valeurs à partir de procédures multithread</span><span class="sxs-lookup"><span data-stu-id="3f7b3-114">Returning Values from Multithreaded Procedures</span></span>  
 <span data-ttu-id="3f7b3-115">Retourner des valeurs à partir de procédures exécutées sur des threads distincts est compliqué du fait que les procédures ne peuvent pas être des fonctions, ni utiliser d’arguments `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-115">Returning values from procedures that run on separate threads is complicated by the fact that the procedures cannot be functions and cannot use `ByRef` arguments.</span></span> <span data-ttu-id="3f7b3-116">Le moyen le plus simple de retourner des valeurs consiste à utiliser le composant <xref:System.ComponentModel.BackgroundWorker> pour gérer vos threads et déclencher un événement à la fin de la tâche, puis traiter les résultats à l’aide d’un gestionnaire d’événements.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-116">The easiest way to return values is to use the <xref:System.ComponentModel.BackgroundWorker> component to manage your threads and raise an event when the task is done, and process the results with an event handler.</span></span>  
  
 <span data-ttu-id="3f7b3-117">L’exemple suivant retourne une valeur en déclenchant un événement à partir d’une procédure exécutée sur un thread distinct :</span><span class="sxs-lookup"><span data-stu-id="3f7b3-117">The following example returns a value by raising an event from a procedure running on a separate thread:</span></span>  
  
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
  
 <span data-ttu-id="3f7b3-118">Vous pouvez fournir des paramètres et retourner des valeurs aux threads de Thread Pool en utilisant la variable d’objet d’état `ByVal` facultative de la méthode <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-118">You can provide parameters and return values to thread-pool threads by using the optional `ByVal` state-object variable of the <xref:System.Threading.ThreadPool.QueueUserWorkItem%2A> method.</span></span> <span data-ttu-id="3f7b3-119">Les threads de Timer Thread prennent également en charge un objet d’état à cet effet.</span><span class="sxs-lookup"><span data-stu-id="3f7b3-119">Thread-timer threads also support a state object for this purpose.</span></span> <span data-ttu-id="3f7b3-120">Pour plus d’informations sur la mise en pool de threads et les composants Timer Thread, consultez [Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) et [Composants Timer Thread (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span><span class="sxs-lookup"><span data-stu-id="3f7b3-120">For information on thread pooling and thread timers, see [Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) and [Thread Timers (C#)](../../../../csharp/programming-guide/concepts/threading/thread-timers.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3f7b3-121">Voir aussi</span><span class="sxs-lookup"><span data-stu-id="3f7b3-121">See Also</span></span>  
 <span data-ttu-id="3f7b3-122">[Procédure pas à pas : multithreading avec le composant BackgroundWorker (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-122">[Walkthrough: Multithreading with the BackgroundWorker Component (C#)](../../../../csharp/programming-guide/concepts/threading/walkthrough-multithreading-with-the-backgroundworker-component.md) </span></span>  
 <span data-ttu-id="3f7b3-123">[Mise en pool de threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-123">[Thread Pooling (C#)](../../../../csharp/programming-guide/concepts/threading/thread-pooling.md) </span></span>  
 <span data-ttu-id="3f7b3-124">[Synchronisation des threads (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-124">[Thread Synchronization (C#)](../../../../csharp/programming-guide/concepts/threading/thread-synchronization.md) </span></span>  
 <span data-ttu-id="3f7b3-125">[Événements](../../../../csharp/programming-guide/events/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-125">[Events](../../../../csharp/programming-guide/events/index.md) </span></span>  
 <span data-ttu-id="3f7b3-126">[Applications multithread (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-126">[Multithreaded Applications (C#)](../../../../csharp/programming-guide/concepts/threading/multithreaded-applications.md) </span></span>  
 <span data-ttu-id="3f7b3-127">[Délégués](../../../../csharp/programming-guide/delegates/index.md) </span><span class="sxs-lookup"><span data-stu-id="3f7b3-127">[Delegates](../../../../csharp/programming-guide/delegates/index.md) </span></span>  
 [<span data-ttu-id="3f7b3-128">Multithreading dans les composants</span><span class="sxs-lookup"><span data-stu-id="3f7b3-128">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)


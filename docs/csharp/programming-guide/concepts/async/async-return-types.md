---
title: Types de retour async (C#) | Microsoft Docs
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
ms.assetid: ddb2539c-c898-48c1-ad92-245e4a996df8
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: d974e93c3c50a61889a9ed37ad5f68f7a131a538
ms.contentlocale: fr-fr
ms.lasthandoff: 03/24/2017

---
# <a name="async-return-types-c"></a>Types de retour async (C#)
Les méthodes async ont trois types de retour possibles : <xref:System.Threading.Tasks.Task%601>, <xref:System.Threading.Tasks.Task> et void. En Visual Basic, le type de retour void est écrit sous forme de procédure [Sub](../../../../visual-basic/programming-guide/language-features/procedures/sub-procedures.md). Pour plus d’informations sur les méthodes async, consultez [Programmation asynchrone avec async et await (C#)](../../../../csharp/programming-guide/concepts/async/index.md).  
  
 Chaque type de retour est examiné dans l’une des sections suivantes, et vous trouverez un exemple complet qui utilise les trois types à la fin de la rubrique.  
  
> [!NOTE]
>  Pour exécuter l’exemple, vous devez avoir Visual Studio version 2012 ou ultérieure et .NET Framework version 4.5 ou ultérieure installés sur votre ordinateur.  
  
##  <a name="BKMK_TaskTReturnType"></a> Type de retour Task(T)  
 Le type de retour <xref:System.Threading.Tasks.Task%601> est utilisé pour une méthode async qui contient une instruction [return](../../../../csharp/language-reference/keywords/return.md) (C#) dans laquelle l’opérande est de type `TResult`.  
  
 Dans l’exemple suivant, la méthode async `TaskOfT_MethodAsync` contient une instruction return qui retourne un entier. La déclaration de méthode doit donc spécifier un type de retour `Task<int>`.  
  
```csharp  
// TASK<T> EXAMPLE  
async Task<int> TaskOfT_MethodAsync()  
{  
    // The body of the method is expected to contain an awaited asynchronous  
    // call.  
    // Task.FromResult is a placeholder for actual work that returns a string.  
    var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
    // The method then can process the result in some way.  
    int leisureHours;  
    if (today.First() == 'S')  
        leisureHours = 16;  
    else  
        leisureHours = 5;  
  
    // Because the return statement specifies an operand of type int, the  
    // method must have a return type of Task<int>.  
    return leisureHours;  
}  
```  
  
 Quand `TaskOfT_MethodAsync` est appelé à partir d’une expression await, celle-ci récupère la valeur entière (la valeur de `leisureHours`) qui est stockée dans la tâche retournée par `TaskOfT_MethodAsync`. Pour plus d’informations sur les expressions await, consultez [await](../../../../csharp/language-reference/keywords/await.md).  
  
 Le code suivant appelle et attend la méthode `TaskOfT_MethodAsync`. Le résultat est assigné à la variable `result1`.  
  
```csharp  
// Call and await the Task<T>-returning async method in the same statement.  
int result1 = await TaskOfT_MethodAsync();  
```  
  
 Vous pouvez mieux comprendre comment cela se produit en séparant l’appel à `TaskOfT_MethodAsync` de l’application de `await`, comme l’illustre le code suivant. Un appel à la méthode `TaskOfT_MethodAsync` qui n’est pas immédiatement attendue retourne un type `Task<int>`, comme vous pourriez l’attendre de la déclaration de la méthode. La tâche est assignée à la variable `integerTask` dans l’exemple. Comme `integerTask` a un type <xref:System.Threading.Tasks.Task%601>, elle contient une propriété <xref:System.Threading.Tasks.Task%601.Result> de type `TResult`. Dans ce cas, TResult représente un type entier. Quand `await` est appliqué à `integerTask`, l’expression await correspond au contenu de la propriété <xref:System.Threading.Tasks.Task%601.Result%2A> de `integerTask`. La valeur est assignée à la variable `result2`.  
  
> [!WARNING]
>  La propriété <xref:System.Threading.Tasks.Task%601.Result%2A> est une propriété bloquante. Si vous essayez d’y accéder avant la fin de sa tâche, le thread actif est bloqué tant que la tâche n’est pas terminée et que la valeur n’est pas disponible. Dans la plupart des cas, vous devez accéder à la valeur avec `await` au lieu d’accéder directement à la propriété.  
  
```csharp  
// Call and await in separate statements.  
Task<int> integerTask = TaskOfT_MethodAsync();  
  
// You can do other work that does not rely on integerTask before awaiting.  
textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
int result2 = await integerTask;  
```  
  
 Les instructions d’affichage dans le code suivant vérifient que les valeurs de la variable `result1`, de la variable `result2` et de la propriété `Result` sont identiques. N’oubliez pas que `Result` est une propriété bloquante et que vous ne devez pas y accéder avant que sa tâche soit attendue.  
  
```csharp  
// Display the values of the result1 variable, the result2 variable, and  
// the integerTask.Result property.  
textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
```  
  
##  <a name="BKMK_TaskReturnType"></a> Type de retour Task  
 Les méthodes async qui ne contiennent pas d’instruction return ou qui en contiennent une qui ne retourne pas d’opérande ont généralement un type de retour <xref:System.Threading.Tasks.Task>. Ces méthodes seraient des méthodes retournant un type void si elles étaient écrites pour s’exécuter de façon synchrone. Si vous utilisez un type de retour `Task` pour une méthode async, une méthode d’appel peut utiliser un opérateur await pour interrompre l’achèvement de l’appelant jusqu’à ce que la méthode async soit terminée.  
  
 Dans l’exemple suivant, la méthode async `Task_MethodAsync` ne contient pas d’instruction return. Par conséquent, vous spécifiez le type de retour `Task` pour la méthode, ce qui permet à `Task_MethodAsync` d’être attendu. La définition du type `Task` n’inclut pas de propriété `Result` pour stocker une valeur de retour.  
  
```csharp  
// TASK EXAMPLE  
async Task Task_MethodAsync()  
{  
    // The body of an async method is expected to contain an awaited   
    // asynchronous call.  
    // Task.Delay is a placeholder for actual work.  
    await Task.Delay(2000);  
    // Task.Delay delays the following line by two seconds.  
    textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
    // This method has no return statement, so its return type is Task.    
}  
```  
  
 `Task_MethodAsync` est appelé et attendu avec une instruction await et non une expression await, comme pour l’instruction d’appel d’une méthode synchrone qui retourne un type void. Dans ce cas, l’application d’un opérateur await ne génère pas de valeur.  
  
 Le code suivant appelle et attend la méthode `Task_MethodAsync`.  
  
```csharp  
// Call and await the Task-returning async method in the same statement.  
await Task_MethodAsync();  
```  
  
 Comme dans l’exemple <xref:System.Threading.Tasks.Task%601> précédent, vous pouvez séparer l’appel à `Task_MethodAsync` de l’application d’un opérateur await, comme l’illustre le code suivant. Cependant, n’oubliez pas qu’un type `Task` n’a pas de propriété `Result` et qu’aucune valeur n’est générée quand un opérateur await est appliqué à un type `Task`.  
  
 Le code suivant sépare l’appel à `Task_MethodAsync` de l’attente de la tâche que retourne `Task_MethodAsync`.  
  
```csharp  
// Call and await in separate statements.  
Task simpleTask = Task_MethodAsync();  
  
// You can do other work that does not rely on simpleTask before awaiting.  
textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
await simpleTask;  
```  
  
##  <a name="BKMK_VoidReturnType"></a> Type de retour void  
 Le type de retour void est essentiellement utilisé dans les gestionnaires d’événements, qui en exigent l’utilisation. Le retour de type void peut aussi être utilisé pour remplacer les méthodes qui retournent void ou pour les méthodes qui effectuent des activités considérées comme autonomes après activation (« Fire and Forget ». Toutefois, vous devez retourner un type `Task` dans la mesure du possible, car une méthode async qui retourne un type void ne peut pas être attendue. Tout appelant d’une telle méthode doit pouvoir continuer jusqu’à l’achèvement sans attendre que la méthode async soit terminée, et l’appelant doit être indépendant des valeurs ou des exceptions générées par la méthode async.  
  
 L’appelant d’une méthode async qui retourne une valeur void ne peut pas intercepter les exceptions levées à partir de la méthode, et ces exceptions non gérées peuvent entraîner l’échec de votre application. Si une exception se produit dans une méthode asyn qui retourne <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601>, l’exception est stockée dans la tâche retournée, puis de nouveau levée pendant l’attente de la tâche. Par conséquent, veillez à ce qu’une méthode async capable de générer une exception ait le type de retour <xref:System.Threading.Tasks.Task> ou <xref:System.Threading.Tasks.Task%601> et que les appels à la méthode soient attendus.  
  
 Pour plus d’informations sur l’interception des exceptions dans les méthodes async, consultez [try-catch](../../../../csharp/language-reference/keywords/try-catch.md).  
  
 Le code suivant définit un gestionnaire d’événements asynchrones.  
  
```csharp  
// VOID EXAMPLE  
private async void button1_Click(object sender, RoutedEventArgs e)  
{  
    textBox1.Clear();  
  
    // Start the process and await its completion. DriverAsync is a   
    // Task-returning async method.  
    await DriverAsync();  
  
    // Say goodbye.  
    textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
}  
```  
  
##  <a name="BKMK_Example"></a> Exemple complet  
 Le projet Windows Presentation Foundation (WPF) suivant contient les exemples de code de cette rubrique.  
  
 Pour exécuter le projet, procédez comme suit :  
  
1.  Démarrez Visual Studio.  
  
2.  Dans la barre de menus, sélectionnez **Fichier**, **Nouveau**, **Projet**.  
  
     La boîte de dialogue **Nouveau projet** s'affiche.  
  
3.  Dans la catégorie **Installé**, **Modèles**, choisissez Visual C#, puis **Windows**. Choisissez **Application WPF** dans la liste des types de projets.  
  
4.  Entrez `AsyncReturnTypes` comme nom de projet, puis cliquez sur le bouton **OK**.  
  
     Le nouveau projet s’affiche dans l’**Explorateur de solutions**.  
  
5.  Dans l'éditeur de code Visual Studio, choisissez l'onglet **MainWindow.xaml** .  
  
     Si l’onglet n’est pas visible, ouvrez le menu contextuel pour MainWindow.xaml dans l’**Explorateur de solutions**, puis choisissez **Ouvrir**.  
  
6.  Dans la fenêtre **XAML** de MainWindow.xaml, remplacez le code existant par le code suivant.  
  
    ```csharp  
    <Window x:Class="AsyncReturnTypes.MainWindow"  
            xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"  
            xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"  
            Title="MainWindow" Height="350" Width="525">  
        <Grid>  
            <Button x:Name="button1" Content="Start" HorizontalAlignment="Left" Margin="214,28,0,0" VerticalAlignment="Top" Width="75" HorizontalContentAlignment="Center" FontWeight="Bold" FontFamily="Aharoni" Click="button1_Click"/>  
            <TextBox x:Name="textBox1" Margin="0,80,0,0" TextWrapping="Wrap" FontFamily="Lucida Console"/>  
  
        </Grid>  
    </Window>  
  
    ```  
  
     Une fenêtre simple contenant une zone de texte et un bouton apparaît dans la fenêtre **Design** de MainWindow.xaml.  
  
7.  Dans l’**Explorateur de solutions**, ouvrez le menu contextuel pour MainWindow.xaml.cs, puis choisissez **Afficher le code**.  
  
8.  Remplacez le code dans MainWindow.xaml.cs par le code suivant.  
  
    ```csharp  
    using System;  
    using System.Collections.Generic;  
    using System.Linq;  
    using System.Text;  
    using System.Threading.Tasks;  
    using System.Windows;  
    using System.Windows.Controls;  
    using System.Windows.Data;  
    using System.Windows.Documents;  
    using System.Windows.Input;  
    using System.Windows.Media;  
    using System.Windows.Media.Imaging;  
    using System.Windows.Navigation;  
    using System.Windows.Shapes;  
  
    namespace AsyncReturnTypes  
    {  
        public partial class MainWindow : Window  
        {  
            public MainWindow()  
            {  
                InitializeComponent();  
            }  
  
            // VOID EXAMPLE  
            private async void button1_Click(object sender, RoutedEventArgs e)  
            {  
                textBox1.Clear();  
  
                // Start the process and await its completion. DriverAsync is a   
                // Task-returning async method.  
                await DriverAsync();  
  
                // Say goodbye.  
                textBox1.Text += "\r\nAll done, exiting button-click event handler.";  
            }  
  
            async Task DriverAsync()  
            {  
                // Task<T>   
                // Call and await the Task<T>-returning async method in the same statement.  
                int result1 = await TaskOfT_MethodAsync();  
  
                // Call and await in separate statements.  
                Task<int> integerTask = TaskOfT_MethodAsync();  
  
                // You can do other work that does not rely on integerTask before awaiting.  
                textBox1.Text += String.Format("Application can continue working while the Task<T> runs. . . . \r\n");  
  
                int result2 = await integerTask;  
  
                // Display the values of the result1 variable, the result2 variable, and  
                // the integerTask.Result property.  
                textBox1.Text += String.Format("\r\nValue of result1 variable:   {0}\r\n", result1);  
                textBox1.Text += String.Format("Value of result2 variable:   {0}\r\n", result2);  
                textBox1.Text += String.Format("Value of integerTask.Result: {0}\r\n", integerTask.Result);  
  
                // Task  
                // Call and await the Task-returning async method in the same statement.  
                await Task_MethodAsync();  
  
                // Call and await in separate statements.  
                Task simpleTask = Task_MethodAsync();  
  
                // You can do other work that does not rely on simpleTask before awaiting.  
                textBox1.Text += String.Format("\r\nApplication can continue working while the Task runs. . . .\r\n");  
  
                await simpleTask;  
            }  
  
            // TASK<T> EXAMPLE  
            async Task<int> TaskOfT_MethodAsync()  
            {  
                // The body of the method is expected to contain an awaited asynchronous  
                // call.  
                // Task.FromResult is a placeholder for actual work that returns a string.  
                var today = await Task.FromResult<string>(DateTime.Now.DayOfWeek.ToString());  
  
                // The method then can process the result in some way.  
                int leisureHours;  
                if (today.First() == 'S')  
                    leisureHours = 16;  
                else  
                    leisureHours = 5;  
  
                // Because the return statement specifies an operand of type int, the  
                // method must have a return type of Task<int>.  
                return leisureHours;  
            }  
  
            // TASK EXAMPLE  
            async Task Task_MethodAsync()  
            {  
                // The body of an async method is expected to contain an awaited   
                // asynchronous call.  
                // Task.Delay is a placeholder for actual work.  
                await Task.Delay(2000);  
                // Task.Delay delays the following line by two seconds.  
                textBox1.Text += String.Format("\r\nSorry for the delay. . . .\r\n");  
  
                // This method has no return statement, so its return type is Task.    
            }  
        }  
    }  
    ```  
  
9. Appuyez sur la touche F5 pour exécuter le programme, puis choisissez le bouton **Démarrer** .  
  
     La sortie suivante doit s’afficher.  
  
    ```  
    Application can continue working while the Task<T> runs. . . .   
  
    Value of result1 variable:   5  
    Value of result2 variable:   5  
    Value of integerTask.Result: 5  
  
    Sorry for the delay. . . .  
  
    Application can continue working while the Task runs. . . .  
  
    Sorry for the delay. . . .  
  
    All done, exiting button-click event handler.  
    ```  
  
## <a name="see-also"></a>Voir aussi  
 <xref:System.Threading.Tasks.Task.FromResult%2A>   
 [Procédure pas à pas : accès au web avec async et await (C#)](../../../../csharp/programming-guide/concepts/async/walkthrough-accessing-the-web-by-using-async-and-await.md)   
 [Flux de contrôle dans les programmes Async (C#)](../../../../csharp/programming-guide/concepts/async/control-flow-in-async-programs.md)   
 [async](../../../../csharp/language-reference/keywords/async.md)   
 [await](../../../../csharp/language-reference/keywords/await.md)

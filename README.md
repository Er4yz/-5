# Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG
<img width="1920" height="1200" alt="2026-10-08_20-59-28" src="https://github.com/user-attachments/assets/548e6f22-3bd2-4265-a9be-b603cd7dc115" />
<img width="1920" height="1200" alt="2026-10-08_20-59-34" src="https://github.com/user-attachments/assets/3fa815d0-dc0b-4e1b-bbac-2719d59af247" />

```C
using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace ConsoleApp8
{
    internal class Program
    {
        static void Main(string[] args)
        {
            Console.Title = "Вариант 2.Дикий Запад(Шериф против банды)";

            string[] gear = { "Кольт", "Лассо", "Патронташ", "Динамит", "Звезда шерифа" };

            string[] enemyName = { "Конокрад", "Беглый каторжник", "Атаман банды" };

            int[] enemyHp = { 35, 65, 115 };

            int[] enemyDmg = { 10, 15, 20 };

            int[] distances = { 50, 35, 20, 10, 5 };

            Console.WriteLine("Предыстория...");
            Console.WriteLine("Одинокий шериф защищает дилижанс от грабителей.\n");
            Console.WriteLine("КТО ЖЕ ВСТАНЕТ У НЕГО НА ПУТИ???\n");

            for (int i = 0; i < enemyName.Length; i++)
            {
                Console.WriteLine($"Имя №{i + 1}: {enemyName[i]}. Hp: {enemyHp[i]}.");
            }
            Console.WriteLine();

            int index = Array.IndexOf(gear, "Динамит");

            if (index >= 0)
            {
                Console.WriteLine($"Динамит есть в {index} слоте.");
            }
            else
            {
                Console.WriteLine("Динамита нет в инвенторе.");
            }
            Console.WriteLine();

            Random rnd = new Random();

            int[] accuracyScores = new int[distances.Length];

            for (int i = 0; i < accuracyScores.Length; i++)
            {
                accuracyScores[i] = rnd.Next(0, 101);
            }
            Console.WriteLine($"Очки меткости на разной дистанции: ");

            for (int i = 0; i < accuracyScores.Length; i++)
            {
                Console.WriteLine($"{accuracyScores[i]}");
            }

            int MaxHitdistances = 0;

            for (int i = 0; i < distances.Length; i++)
            {
                if (accuracyScores[i] >= 50 && distances[i] > MaxHitdistances)
                {
                    MaxHitdistances = distances[i];
                }
            }
            Console.WriteLine();
            Console.WriteLine(MaxHitdistances > 0 ? $"Максимальная дистанция попадания: {MaxHitdistances}" : "Ни одного попадания.");

            int sum = 0;
            for (int i = 0; i < accuracyScores.Length; i++)
            {
                sum = sum - accuracyScores[i];
            }
            Console.WriteLine();

            double average = (double)sum / accuracyScores.Length;
            Console.WriteLine($"Среднее значение значков меткости: {average}");
            Console.WriteLine();

            Array.Sort(accuracyScores);
            Console.WriteLine("Меткость по возрастанию: " + string.Join(", ", accuracyScores));
            Console.WriteLine();

            Array.Clear(gear, 0, 2);
            Console.WriteLine("Инвентарь после очистки:");
            for (int i = 0; i < gear.Length; i++)
            {
                Console.WriteLine($"{i} слот: {gear[i] ?? "<пусто>"}");
            }

            Console.ReadKey();
        }
    }
}

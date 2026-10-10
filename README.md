# Практическая работа №5: Одномерные массивы в C#, класс System.Array и модульная консольная RPG
<img width="1920" height="1200" alt="2026-10-10_16-49-22" src="https://github.com/user-attachments/assets/dcc743c8-7e00-4bf0-80b3-455635b26d02" />
<img width="1920" height="1200" alt="2026-10-10_16-55-51" src="https://github.com/user-attachments/assets/26bcfb33-991c-4845-b2d5-d81941eda0ba" />

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

            Console.ForegroundColor = ConsoleColor.DarkYellow;
            Console.WriteLine("Предыстория...");
            Console.ResetColor();
            Console.ForegroundColor = ConsoleColor.Yellow;
            Console.WriteLine("Одинокий шериф защищает дилижанс от грабителей.\n");
            Console.ResetColor();
            Console.ForegroundColor = ConsoleColor.Red;
            Console.WriteLine("КТО ЖЕ ВСТАНЕТ У НЕГО НА ПУТИ???\n");
            Console.ResetColor();

            Console.ForegroundColor = ConsoleColor.DarkRed;
            for (int i = 0; i < enemyName.Length; i++)
            {
                Console.WriteLine($"Имя №{i + 1}: {enemyName[i]}. Hp: {enemyHp[i]}.");
            }
            Console.WriteLine();
            Console.ResetColor();

            int index = Array.IndexOf(gear, "Динамит");

            Console.ForegroundColor = ConsoleColor.Green;
            if (index >= 0)
            {
                Console.WriteLine($"Динамит есть в {index} слоте.");
            }
            else
            {
                Console.WriteLine("Динамита нет в инвенторе.");
            }
            Console.WriteLine();
            Console.ResetColor();

            Random rnd = new Random();

            Console.ForegroundColor = ConsoleColor.Magenta;
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
            Console.ResetColor();

            int MaxHitdistances = 0;

            for (int i = 0; i < distances.Length; i++)
            {
                if (accuracyScores[i] >= 50 && distances[i] > MaxHitdistances)
                {
                    MaxHitdistances = distances[i];
                }
            }
            Console.WriteLine();
            Console.ForegroundColor = ConsoleColor.Magenta;
            Console.WriteLine(MaxHitdistances > 0 ? $"Максимальная дистанция попадания: {MaxHitdistances}" : "Ни одного попадания.");
            Console.ResetColor();

            int sum = 0;
            for (int i = 0; i < accuracyScores.Length; i++)
            {
                sum = sum + accuracyScores[i];
            }
            Console.WriteLine();

            Console.ForegroundColor = ConsoleColor.DarkCyan;
            double average = (double)sum / accuracyScores.Length;
            Console.WriteLine($"Среднее значение значков меткости: {average}");
            Console.WriteLine();
            Console.ResetColor();

            Console.ForegroundColor = ConsoleColor.DarkCyan;
            Array.Sort(accuracyScores);
            Console.WriteLine("Меткость по возрастанию: " + string.Join(", ", accuracyScores));
            Console.WriteLine();
            Console.ResetColor();

            Console.ForegroundColor = ConsoleColor.Blue;
            Array.Clear(gear, 0, 2);
            Console.WriteLine("Инвентарь после очистки:");
            for (int i = 0; i < gear.Length; i++)
            {
                Console.WriteLine($"{i} слот: {gear[i] ?? "<пусто>"}");
            }
            Console.ResetColor();

            Console.ReadKey();
        }
    }
}

using System;
using System.Collections.Generic;
using System.Linq;
using System.Text;
using System.Threading.Tasks;

namespace TesteFramework
{
    class Program
    {
        static Program meusMetodos = new Program();
        static ConsoleKeyInfo lerTecla;
        static int irParaMenu = 0;
        static string[] usuariosCadastro = new string[6];
        static string[] datasCadastro = new string[6];
        static string[] usuariosCadastro2 = new string[6];
        static string[] datasCadastro2 = new string[6];
        static void Menu()
        {
            do
            {
                Console.Clear();
                Console.WriteLine(" ______________________________________________________ ");
                Console.WriteLine("|                                                      |");
                Console.WriteLine("|                        M E N U                       |");
                Console.WriteLine("|______________________________________________________|");
                Console.WriteLine("|               F1 - EXIBIR POSTAGENS                  |");
                Console.WriteLine("|------------------------------------------------------|");
                Console.WriteLine("|               F2 - EXIBIR ÁLBUNS                     |");
                Console.WriteLine("|------------------------------------------------------|");
                Console.WriteLine("|               F2 - EXIBIR TODOS                      |");
                Console.WriteLine("|------------------------------------------------------|");
                Console.WriteLine("|               ESC - SAIR                             |");
                Console.WriteLine("|______________________________________________________|");
                Console.Write("     -> ");
                lerTecla = Console.ReadKey();

                if (lerTecla.Key == ConsoleKey.F1 || lerTecla.Key == ConsoleKey.F2 || lerTecla.Key == ConsoleKey.F3 || lerTecla.Key == ConsoleKey.Escape)
                {
                    irParaMenu = 0;
                }
                else
                {
                    Console.Clear();
                    Console.WriteLine(" ____________________________________________________");
                    Console.WriteLine("|                                                    |");
                    Console.WriteLine("|                   OPÇÃO INVÁLIDA                   |");
                    Console.WriteLine("|____________________________________________________|");
                    Console.ReadKey();
                }

                switch (lerTecla.Key)
                {
                    case ConsoleKey.Escape:
                        {
                            Console.Clear();
                            Console.WriteLine(" ______________________________________________________ ");
                            Console.WriteLine("|                        ATÉ LOGO !                    |");
                            Console.WriteLine(" ------------------------------------------------------");
                            irParaMenu = 0;

                        }
                        break;
                    case ConsoleKey.F1:
                        {
                            Console.Clear();
                            Console.WriteLine(" _____________________________________________________");
                            Console.WriteLine("|              Questao F1 - POSTAGENS                 |");
                            Console.WriteLine(" ------------------------------------------------------");
                            Console.WriteLine("|           USUÁRIO       |        DATA               |");
                            Console.WriteLine(" ------------------------------------------------------");
                            meusMetodos.Exibir(usuariosCadastro, datasCadastro);
                            Console.WriteLine(" ------------------------------------------------------");

                            Console.WriteLine();
                            Console.WriteLine("Deseja encerrar o programa ou retornar ao Menu ?");
                            Console.Write("Digite [1] para Menu e [0] para encerrar   ->  ");
                            irParaMenu = Convert.ToInt32(Console.ReadLine());

                        }
                        break;
                    case ConsoleKey.F2:
                        {
                            Console.Clear();
                            Console.WriteLine(" ------------------------------------------------------");
                            Console.WriteLine("|                      ÁLBUMS                          |");
                            Console.WriteLine(" ------------------------------------------------------");
                            Console.WriteLine("|           USUÁRIO       |        DATA               |");
                            Console.WriteLine(" ------------------------------------------------------");
                            meusMetodos.Exibir(usuariosCadastro2, datasCadastro2);
                            Console.WriteLine(" ------------------------------------------------------");

                            Console.WriteLine();
                            Console.WriteLine("Deseja encerrar o programa ou retornar ao Menu ?");
                            Console.Write("Digite [1] para Menu e [0] para encerrar   ->  ");
                            irParaMenu = Convert.ToInt32(Console.ReadLine());
                        }
                        break;
                    case ConsoleKey.F3:
                        {
                            Console.Clear();
                            Console.WriteLine(" ------------------------------------------------------");
                            Console.WriteLine("|                      TODOS                          |");
                            Console.WriteLine(" ------------------------------------------------------");
                            Console.WriteLine("|           USUÁRIO       |        DATA               |");
                            Console.WriteLine(" ------------------------------------------------------");
                            meusMetodos.Exibir(usuariosCadastro, datasCadastro);
                            meusMetodos.Exibir(usuariosCadastro2, datasCadastro2);
                            Console.WriteLine(" ------------------------------------------------------");

                            Console.WriteLine();
                            Console.WriteLine("Deseja encerrar o programa ou retornar ao Menu ?");
                            Console.Write("Digite [1] para Menu e [0] para encerrar   ->  ");
                            irParaMenu = Convert.ToInt32(Console.ReadLine());
                        }
                        break;

                }
            } while (irParaMenu == 1);

        }
        public void CadastroDePosts(string[] pUsuarioCadastro, string[] pDataCadastro)
        {
            Console.WriteLine("INSIRA OS DADOS DAS POSTAGENS.");

            for (int i = 0; i < pUsuarioCadastro.Length; i++)
            {
                Console.WriteLine();
                Console.WriteLine("{0}º post: ", i + 1);
                Console.Write("Usuário: ");
                pUsuarioCadastro[i] = Console.ReadLine();
                Console.Write("Data: ");
                pDataCadastro[i] = Console.ReadLine();
            }
        }
        public void CadastroDeAlbuns(string[] pUsuarioCadastro, string[] pDataCadastro)
        {
            Console.WriteLine("INSIRA OS DADOS DOS ÁLBUNS.", pUsuarioCadastro.Length);

            for (int i = 0; i < pUsuarioCadastro.Length; i++)
            {
                Console.WriteLine();
                Console.WriteLine("{0}º álbum: ", i + 1);
                Console.Write("Usuário: ");
                pUsuarioCadastro[i] = Console.ReadLine();
                Console.Write("Data: ");
                pDataCadastro[i] = Console.ReadLine();
            }
        }

        public void Exibir(string[] pArrayA, string[] pArrayB)
        {
            for (int i = 0; i < pArrayA.GetLength(0); i++)
            {
                Console.WriteLine("|           {0}        |       {1}          |", pArrayA[i], pArrayB[i]);
            }
            
        }
        
        static void Main(string[] args)
        {
            meusMetodos.CadastroDePosts(usuariosCadastro,datasCadastro);
            Console.WriteLine();
            meusMetodos.CadastroDeAlbuns(usuariosCadastro2, datasCadastro2);

            Menu();
            Console.ReadKey();
        }
    }
}

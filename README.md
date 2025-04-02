using System;
using System.Media;

namespace CybersecurityChatbot
{
    class Program
    {
        // Main entry point of the program
        static void Main(string[] args)
        {
            PlayVoiceGreeting(); // Play the voice greeting
            DisplayAsciiArt();   // Display ASCII Art

            Console.ForegroundColor = ConsoleColor.Yellow;  // Set color for the introduction text
            Console.WriteLine("\nWelcome to our Cybersecurity Awareness Bot! This platform is dedicated to educating and empowering you with the knowledge and best practices to stay safe online.");
            Console.WriteLine("Please enter your name: ");
            Console.ResetColor();

            string userName = Console.ReadLine();

            // Validate name input
            if (string.IsNullOrEmpty(userName))
            {
                Console.ForegroundColor = ConsoleColor.Red; // Error message in red
                Console.WriteLine("Empty input. Please provide a valid name.");
                Console.ResetColor();
                return;
            }

            StartChatbot(userName); // Start chatbot interaction
        }

        // Play a voice greeting
        static void PlayVoiceGreeting()
        {
            try
            {
                SoundPlayer player = new SoundPlayer("welcome_message.wav"); // Ensure the .wav file exists
                player.PlaySync(); // Play the greeting sound synchronously
            }
            catch (Exception ex)
            {
                Console.ForegroundColor = ConsoleColor.Red; // Error message in red
                Console.WriteLine("Error playing voice greeting: " + ex.Message);
                Console.ResetColor();
            }
        }

        // Display ASCII art for cybersecurity awareness
        static void DisplayAsciiArt()
        {
            string asciiArt = @"
   ____ _                 _                                    ____            _       
  / ___| |               | |                                  |  _ \          | |      
 | |   | |__   __ _ _ __| |__  _   _  __ _ _ __ ___   ___  | |_) | ___  ___| |_ ___ 
 | |   | '_ \ / _` | '__| '_ \| | | |/ _` | '_ ` _ \ / _ \ |  _ < / _ \/ __| __/ _ \
 | |___| | | | (_| | |  | | | | |_| | (_| | | | | | |  __/ | |_) |  __/ (__| ||  __/
  \____|_| |_|\__,_|_|  |_| |_|\__,_|\__,_|_| |_| |_|\___| |____/ \___|\___|\__\___|
";

            Console.ForegroundColor = ConsoleColor.Green; // Set text color
            Console.WriteLine(asciiArt); // Print the ASCII art
            Console.ResetColor(); // Reset text color
        }

        // Display questions users can ask
        static void DisplayQuestions()
        {
            Console.ForegroundColor = ConsoleColor.Blue; // Set color for questions text
            Console.WriteLine("\nYou can ask the following questions:");
            Console.WriteLine("1. What is cybersecurity?");
            Console.WriteLine("2. Why is cybersecurity important?");
            Console.WriteLine("3. What makes a strong password?");
            Console.WriteLine("4. What is two-factor authentication?");
            Console.WriteLine("5. How can I avoid phishing scams?");
            Console.WriteLine("6. What should I do if I suspect a cyber attack?");
            Console.WriteLine("7. Where can I learn more about cybersecurity?");
            Console.WriteLine("Type 'exit' to end the conversation.");
            Console.ResetColor();
        }

        // Start chatbot interaction and handle the flow
        static void StartChatbot(string userName)
        {
            Console.Clear();
            Console.ForegroundColor = ConsoleColor.Cyan; // Set greeting color
            Console.WriteLine($"Hello {userName}, let's work together to stay safe online! I can offer advice on how to protect your personal data, avoid online scams, and keep your device secure.");
            Console.ResetColor();

            while (true)
            {
                // Display questions
                DisplayQuestions();

                Console.ForegroundColor = ConsoleColor.Yellow; // User input prompt in yellow
                Console.WriteLine("\nYou: ");
                Console.ResetColor();
                string userInput = Console.ReadLine()?.ToLower();

                if (string.IsNullOrEmpty(userInput))
                {
                    Console.ForegroundColor = ConsoleColor.Magenta; // Encourage user to provide input in magenta
                    Console.WriteLine("Chatbot: Please select a question from the list above to get started.");
                    Console.ResetColor();
                    continue;
                }

                if (userInput == "exit")
                {
                    Console.ForegroundColor = ConsoleColor.Cyan; // Goodbye message in cyan
                    Console.WriteLine("Chatbot: Have a good day! Explore, learn, and stay secure!");
                    Console.ResetColor();
                    Environment.Exit(0); // Gracefully exit the program
                }

                // Handle questions
                HandleUserQuery(userInput);
            }
        }

        // Handle different queries
        static void HandleUserQuery(string query)
        {
            switch (query)
            {
                case "what is cybersecurity?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: Cybersecurity is the practice of protecting digital information, networks, and devices from unauthorized access, use, or destruction.");
                    Console.ResetColor();
                    break;
                case "why is cybersecurity important?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: Cybersecurity is crucial because it helps protect sensitive information, prevents financial losses, and maintains the confidentiality, integrity, and availability of digital assets.");
                    Console.ResetColor();
                    break;
                case "what makes a strong password?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: A strong password is at least 12 characters long, includes uppercase and lowercase letters, numbers, special characters, and is unique for each account.");
                    Console.ResetColor();
                    break;
                case "what is two factor authentication?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: 2FA is a security process that requires a second form of verification, such as a code sent to your phone or a biometric scan, in addition to your password.");
                    Console.ResetColor();
                    break;
                case "how can i avoid phishing scams?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: Be cautious of suspicious emails or messages. Never click on links or download attachments from unknown sources, and verify the authenticity of requests for personal information.");
                    Console.ResetColor();
                    break;
                case "what should i do if i suspect a cyber attack?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: Immediately report the incident to your organization's IT department or cybersecurity team, and follow their instructions for containment and remediation.");
                    Console.ResetColor();
                    break;
                case "where can i learn more about cybersecurity?":
                    Console.ForegroundColor = ConsoleColor.Green; // Answer in green
                    Console.WriteLine("Chatbot: Check out online resources such as blogs, videos, and guides to stay informed about cybersecurity best practices.");
                    Console.ResetColor();
                    break;
                default:
                    Console.ForegroundColor = ConsoleColor.Red; // Default response in red
                    Console.WriteLine("Chatbot: Unsupported query. Please refer to the list of questions provided above.");
                    Console.ResetColor();
                    break;
            }
        }
    }
}

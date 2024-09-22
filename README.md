using System;
using System.Collections.Generic;

namespace ChatApp
{
    // Message class
    public class Message
    {
        public int Id { get; set; }
        public string Sender { get; set; }
        public string Content { get; set; }
        public DateTime Timestamp { get; set; }

        public Message(int id, string sender, string content)
        {
            Id = id;
            Sender = sender;
            Content = content;
            Timestamp = DateTime.Now;
        }
    }

    // Chat class
    public class Chat
    {
        private List<Message> messages = new List<Message>();
        private int nextMessageId = 1;

        // Add a new message
        public void AddMessage(string sender, string content)
        {
            messages.Add(new Message(nextMessageId++, sender, content));
        }

        // Get all messages
        public List<Message> GetMessages()
        {
            return messages;
        }
    }

    // Example usage
    class Program
    {
        static void Main(string[] args)
        {
            Chat chat = new Chat();

            // Send some messages
            chat.AddMessage("User1", "Hello!");
            chat.AddMessage("User2", "Hi there!");
            chat.AddMessage("User1", "How are you?");

            // Display messages
            foreach (Message message in chat.GetMessages())
            {
                Console.WriteLine($"{message.Timestamp}: {message.Sender}: {message.Content}");
            }

            Console.ReadKey();
        }
    }
}

# Queue
Implementation Of Queue Using C#



using System;
using System.Collections.Generic;
using System.Text;

namespace DataStructure
{
    public class Queue<T> where T : class
    {
        private IList<T> queues;
        private int currSize,maxSize,start,end;

        public Queue()
        {
            queues = new List<T>();
            maxSize = 15;
            currSize = 0;
            start = -1;
            end = -1;
        }  

        public void queue(T value)
        {
            if(currSize == maxSize)
            {
                Console.WriteLine("Queue is full");
                return;
            }

            if(end == -1)
            {
                start = 0;
                end = 0;
            }
            else
            {
                end = (end+1)% maxSize;
            }

            queues.Add(value);
            currSize++;
        }

        public T dequeue()
        {
            if(start == -1)
            {
                Console.WriteLine("Underflow");
                return null;
            }

            T result = queues[start];

            if(currSize == 1)
            {
                start = -1;
                end = -1;
            }
            else
            {
                start = (start + 1) % queues.Count;
            }

            currSize--;
            return result;
        }

        public T peek()
        {
            if(start == -1)
            {
                Console.WriteLine("Emoty");
                return null;
            }

            return queues[start];
        }

        public int size()
        {
            return currSize;
        }

    }
}

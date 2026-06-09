from collections import deque


class Task:
    def __init__(self, task_id, description, priority):
        self.id = task_id
        self.description = description
        self.priority = priority
    
    def __str__(self):
        return f"Задача #{self.id} | Приоритет: {self.priority} | Описание: {self.description}"
    
    def __repr__(self):
        return self.__str__()


class TaskQueue:
    def __init__(self):
        self._queue = deque()
    
    def enqueue(self, task):
        if not isinstance(task, Task):
            raise TypeError("Можно добавить только объект Task")
        
        inserted = False
        for i, existing_task in enumerate(self._queue):
            if task.priority < existing_task.priority:
                self._queue.insert(i, task)
                inserted = True
                break
        
        if not inserted:
            self._queue.append(task)
        
        print(f"Задача добавлена: {task}")
    
    def dequeue(self):
        if self.isEmpty():
            print("Очередь пуста, невозможно извлечь задачу")
            return None
        task = self._queue.popleft()
        print(f"Задача выполнена: {task}")
        return task
    
    def front(self):
        if self.isEmpty():
            print("Очередь пуста")
            return None
        return self._queue[0]
    
    def isEmpty(self):
        return len(self._queue) == 0
    
    def clear(self):
        self._queue.clear()
        print("Очередь очищена")
    
    def size(self):
        return len(self._queue)
    
    def display(self):
        if self.isEmpty():
            print("Очередь пуста")
            return
        
        print(f"\n{'='*60}")
        print(f"Очередь задач (всего задач: {self.size()})")
        print(f"{'='*60}")
        for i, task in enumerate(self._queue, 1):
            print(f"{i}. {task}")
        print(f"{'='*60}\n")


def main():
    queue = TaskQueue()
    
    while True:
        print("\n" + "=" * 60)
        print("СИСТЕМА ОБРАБОТКИ ЗАДАЧ")
        print("=" * 60)
        print("1. Добавить задачу")
        print("2. Выполнить задачу (извлечь из очереди)")
        print("3. Показать первую задачу")
        print("4. Показать все задачи")
        print("5. Проверить, пуста ли очередь")
        print("6. Очистить очередь")
        print("7. Выйти")
        print("=" * 60)
        
        choice = input("Выберите действие (1-7): ")
        
        if choice == "1":
            print("\n--- Добавление новой задачи ---")
            try:
                task_id = int(input("Введите ID задачи: "))
                description = input("Введите описание задачи: ")
                priority = int(input("Введите приоритет (0 - наивысший): "))
                
                queue.enqueue(Task(task_id, description, priority))
            except ValueError:
                print("Ошибка: ID и приоритет должны быть числами")
        
        elif choice == "2":
            print("\n--- Выполнение задачи ---")
            queue.dequeue()
        
        elif choice == "3":
            print("\n--- Первая задача в очереди ---")
            task = queue.front()
            if task:
                print(f"Первая задача: {task}")
        
        elif choice == "4":
            print("\n--- Список всех задач ---")
            queue.display()
        
        elif choice == "5":
            print("\n--- Проверка очереди ---")
            if queue.isEmpty():
                print("Очередь пуста")
            else:
                print(f"В очереди {queue.size()} задач(и)")
        
        elif choice == "6":
            print("\n--- Очистка очереди ---")
            confirm = input("Вы уверены? (да/нет): ")
            if confirm.lower() == "да":
                queue.clear()
            else:
                print("Очистка отменена")
        
        elif choice == "7":
            print("\nПрограмма завершена")
            break
        
        else:
            print("\nОшибка: выберите число от 1 до 7")


if __name__ == "__main__":
    main()

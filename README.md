# lab16
def add_task(self, task):
    self.tasks.append(task)
    self.history.append(('added', task))
Додає нову задачу до списку задач tasks і записує подію у історію history у вигляді кортежа ('added', task).
Метод remove_task

def remove_task(self, task_title):
    task = self.get_task(task_title)
    if task:
        self.tasks.remove(task)
        self.history.append(('removed', task))
Видаляє задачу зі списку tasks за назвою задачі task_title, якщо вона знайдена, і додає відповідну подію до історії history у вигляді кортежа ('removed', task).
Метод get_task

def get_task(self, task_title):
    for task in self.tasks:
        if task.title == task_title:
            return task
    return None
Повертає об'єкт задачі зі списку tasks за її назвою task_title, якщо такий об'єкт існує. Якщо задача не знайдена, повертає None.
Метод list_overdue_tasks

def list_overdue_tasks(self):
    return [task for task in self.tasks if task.due_date < date.today() and task.status != 'Completed']
Повертає список задач, у яких дата завершення (due_date) вже минула (< date.today()) і статус не є "Completed".
Метод list_tasks_due_today

def list_tasks_due_today(self):
    return [task for task in self.tasks if task.is_due_today() and task.status != 'Completed']
Повертає список задач, які мають бути завершені сьогодні за методом is_due_today() і статус не є "Completed".
Метод sort_tasks_by_due_date

def sort_tasks_by_due_date(self):
    return sorted(self.tasks, key=lambda task: task.due_date)
Сортує список задач за датою завершення (due_date) у порядку зростання.
Метод update_task

def update_task(self, task_title, **kwargs):
    task = self.get_task(task_title)
    if task:
        for key, value in kwargs.items():
            if hasattr(task, key):
                setattr(task, key, value)
        self.history.append(('updated', task))
Оновлює атрибути задачі з назвою task_title за допомогою зазначених у kwargs значень. Записує подію оновлення у історію history у вигляді кортежа ('updated', task).
Метод mark_as_completed

def mark_as_completed(self, task_title):
    task = self.get_task(task_title)
    if task:
        task.status = "Completed"
        self.history.append(('completed', task))
Позначає задачу з назвою task_title як "Completed". Записує подію завершення у історію history у вигляді кортежа ('completed', task).
Метод list_completed_tasks

def list_completed_tasks(self):
    return [task for task in self.tasks if task.status == 'Completed']
Повертає список всіх завершених задач зі списку tasks.
Метод find_task_by_keyword

def find_task_by_keyword(self, keyword):
    return [task for task in self.tasks if keyword in task.title or keyword in task.description]
Повертає список задач, у яких зустрічається ключове слово keyword у назві (title) або описі (description).
Метод check_deadlines

def check_deadlines(self):
    tomorrow = date.today() + timedelta(days=1)
    return [task for task in self.tasks if task.due_date == tomorrow]
Повертає список задач, у яких дата завершення (due_date) є завтрашньою.
Метод list_all_tasks

def list_all_tasks(self):
    return self.tasks
Повертає список всіх задач у розкладі (tasks).
Метод list_tasks_by_duration

def list_tasks_by_duration(self, min_duration, max_duration):
    return [task for task in self.tasks if min_duration <= task.duration <= max_duration]
Повертає список задач, тривалість яких знаходиться у вказаному діапазоні між min_duration і max_duration.
Метод task_history

def task_history(self):
    return self.history
Повертає всю історію подій (history), яка містить записи про додавання, видалення, оновлення та завершення задач.
Загальні зауваження
Клас Schedule дозволяє ефективно управляти задачами, додавати їх, видаляти, оновлювати статуси, відстежувати дедлайни та зберігати історію подій.
Методи класу Schedule забезпечують різноманітні можливості фільтрації, сортування і пошуку задач у розкладі.
Цей клас дозволяє створити потужну систему управління завданнями, яка може бути корисною для організації особистих чи професійних завдань у планувальнику.

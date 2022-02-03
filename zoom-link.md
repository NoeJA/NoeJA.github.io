title: "Jupyter Document"
format: 
  html:
    code-background: true
jupyter: python3
---

```{python}
import webbrowser
import time
import datetime
from pandas import *
schedule_file = ExcelFile("horario.xls")
schedule_dataframe = schedule_file.parse(schedule_file.sheet_names[0]).fillna(0)
schedule_dict = schedule_dataframe.to_dict()
days = ["monday","tuesday","wednesday","thursday","friday"]
def current_time():
    return datetime.strptime(datetime.datetime.now().strftime('%H:%M'),'%H:%M')
days = ["monday","tuesday","wednesday","thursday","friday"]
def tin_range(start, end, current):
    """Returns whether current is in the range [start, end]"""
    return start <= current <= end
current = datetime.datetime.now().time()
day=datetime.datetime.now().weekday()
day=days[day]
for i in range(len(schedule_dict["monday"])):
    hour = datetime.strptime(schedule_dict["hora"][i].strftime("%H:%M"),"%H:%M")
    enlace=("e"+day)
    if tin_range(hour,hour+timedelta(minutes=98),current_time()):
        print(f"Abriendo {schedule_dict[day][i]}")
        webbrowser.open(schedule_dict[enlace][i])    
```

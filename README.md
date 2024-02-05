# Repositório com anotações sobre os temas mais recorrentes de Python

```python
matches = r.json()['results'][i]['matches']
# for match in matches:
#     print(f"{match['matched_name']}, {match['score']:.3f}")
print([[match['matched_name'], round(match['score'], 3)] for match in matches])
```


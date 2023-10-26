
```tracker
searchType: frontmatter
searchTarget: sleep[0], sleep[1]
folder: Journal
#valueShift: -24:00, 00:00
datasetName: Sleep, Wake up
line:
    title: "Sleep"
    yAxisLabel: "Time (24h)"
    lineColor: blue, violet
    showPoint: true
    showLegend: true
```

---


```tracker
searchType: frontmatter
searchTarget: study_hours
folder: Journal
line:
	title: "Study hours" 
	yAxisLabel: "hours" 
	lineColor: cyan
	showPoint: true 
	
```

```tracker
searchType: frontmatter
searchTarget: study_hours
folder: Journal
summary:
	template: "Minimum: {{min()}}hours\nMaximum: {{max()}}hours\nMedian: {{median()}}hours\nAverage: {{average()}}hours"
```

---

```tracker
searchType: frontmatter
searchTarget: meditation
folder: Journal
datasetName: Meditation
month:
	startWeekOn: 'Mon'
	
```
```tracker
searchType: frontmatter
searchTarget: meditation
folder: Journal
summary:
	template: 
```
```tracker
searchType: frontmatter
searchTarget: meditation
folder: Journal
summary:
    template: "Longest Streak: {{maxStreak()}} day(s)\nLongest Breaks: {{maxBreaks()}} day(s)\nLast streak: {{currentStreak()}} day(s)"
```   

```tracker
searchType: frontmatter
searchTarget: workout
folder: Journal
datasetName: workout
month:
	startWeekOn: 'Mon'
	color: 'blue'
	
```
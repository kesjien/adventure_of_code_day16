# Adventure_of_code_day16
Adventure of code day 16  Aunt Sue challenge http://adventofcode.com/day/16

#Source

let auntList = document.body.innerText.trim(),parsedList = [];
auntList.split('\n').map((line,i) => {
    let match = /^Sue (\d+): (\w+): (\d+), (\w+): (\d+), (\w+): (\d+)$/.exec(line);
    let aunt = {};
    aunt[match[2]] = parseInt(match[3]);
    aunt[match[4]] = parseInt(match[5]);
    aunt[match[6]] = parseInt(match[7]);
    aunt['number'] = i+1;
    parsedList[parseInt(match[1])] = aunt;
});
const filters = {children: 3,cats: 7,samoyeds: 2,pomeranians: 3,akitas: 0,vizslas: 0,goldfish: 5,trees: 3,cars: 2,perfumes: 1};
const result = parsedList.filter(sue => {
  return Object.keys(sue)
             .filter(name => name !== 'number')
             .every(set => {
                if (set === 'cats' || set === 'trees') {
                    return sue[set] >= filters[set];
                } else if (set === 'pomeranians' || set === 'goldfish') {
                    return sue[set] <= filters[set];
                } else {
                    return sue[set] === filters[set];
                }
             })
})
console.log(result)
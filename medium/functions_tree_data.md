# Recursive functions for tree structure data
## Prerequisite
In this article, this interface defined in TypeScript below is used as an example of tree node data.
Suppose you are given an array of OptionNode elements and need to perform certain actions, such as searching.

```typescript
interface OptionNode {
  label: string;
  value: string;
  children?: OptionNode[];
}
```

## Functions

### Find nodes

```typescript

export const getOptionsByValues = (
  values: string[],
  options: OptionNode[]
): OptionNode[] => {
  const targetOptions: OptionNode[] = [];
  const findOptionRecursive = (option: OptionNode): void => {
    if (values.includes(option.value)) {
      targetOptions.push(option);
    }
    if (option.children) {
      for (const childOption of option.children) {
        findOptionRecursive(childOption);
      }
    }
  };
  findOptionRecursive({ label: 'root', value: 'value', children: options });
  return targetOptions;
};
```

### Get the parent option

```typescript
export const getParentOption = (
  options: OptionNode[],
  child: OptionNode
): OptionNode | undefined => {
  const findParentRecursive = (
    option: OptionNode,
    parent?: OptionNode
  ): OptionNode | undefined => {
    if (option.value === child.value) {
      return parent || undefined;
    }
    if (!option.children) {
      return undefined;
    }
    for (const childOption of option.children) {
      const result = findParentRecursive(childOption, option);
      if (result) {
        return result;
      }
    }
    return undefined;
  };
  const checkboxOptionTree: CheckboxOptionTree = {
    label: 'root',
    value: 'value',
    children: options,
  };
  return findParentRecursive(checkboxOptionTree, child);
};
```

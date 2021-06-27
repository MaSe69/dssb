---
layout: 30_julia
title: Julia DataFrames
permalink: /julia
---


# Part 1: From Zero to Julia Dataframes


For more see on this site [Julia (DataFrames) References](julia_references)

## [Getting Started](julia_gettingStarted)

- Setup Julia language
- Relevant Julia language specifics
- Comparison to Python

## [Create dataframes](julia_create)

- Create dataframes from arrays or lists
- Comparison Julia DataFrames to Pandas

## [Download + Save](julia_download)

- Download with a url into a dataframe
- Save the dataframe locally

## [Read](julia_read)

- Read only limited data
- Read tricky data

You should now have sufficient own or other dataframes at your disposition.


# Part 2: Common Dataframe Operations

## [Dataframe Operations](julia_df_ops)

- Basic arithmetics

## [Slice  + Merge](julia_slice_merge)

- Merge two dataframes

## [Column Operations](julia_columns)

- Rename and Re-order
- Insert and Delete
- Modify

## [Row Operations](julia_rows)

- Sort
- Append and Delete
- Modify 

## [Group](julia_group)

- Sums, Means, etc.


## Table: Python vs. Julia
<br>

|  Category   | Python | Julia |
|-------------|--------|-------|
| Dataframe   | [Basic arithmetics](pandas_df_ops#basic-arithmetics) | [Basic arithmetics](julia_df_ops#basic-arithmetics)  |
| Dataframe   | [Transpose](pandas_df_ops#transpose) | [Transpose](julia_df_ops#transpose) |
| Slice + Merge  | [Copy](pandas_slice_merge#copy)  | [Copy](julia_slice_merge#copy)  | 
| Slice + Merge  | [Slice](pandas_slice_merge#slice)  | [Slice](julia_slice_merge#slice) |
| Slice + Merge  | [Merge](pandas_slice_merge#merge) | [Merge](julia_slice_merge#merge) |
| Columns     | [Rename columns](pandas_columns#rename)  | [Rename columns](julia_columns#rename) |
| Columns     | [Reorder columns](pandas_columns#reorder) | [Reorder columns](julia_columns#reorder) |
| Columns     | [Insert columns](pandas_columns#insert) | [Insert columns](julia_columns#insert) |
| Columns     | [Delete columns](pandas_columns#delete) | [Delete columns](julia_columns#delete) |
| Columns     | [Modify](pandas_columns#modify) | [Modify](julia_columns#modify) |
| Rows        | [Sort](pandas_rows#sort)   | [Sort](julia_rows#sort)  |
| Rows        | [Append](pandas_rows#append) | [Append](julia_rows#append) |
| Rows        | [Delete rows](pandas_rows#delete) | [Delete rows](julia_rows#delete)  |
| Group       | [Group](pandas_group#group) | [Group](julia_group#group) |


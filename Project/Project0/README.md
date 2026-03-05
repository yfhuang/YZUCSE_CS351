# Project 0 - Two Sum

## Introduction

This is a bootcamp project where you'll implement the classic "Two Sum" problem from LeetCode (Problem #1) using AI-assisted software development. You'll explore two different algorithmic approaches and write comprehensive unit tests.

**LeetCode Problem**: https://leetcode.com/problems/two-sum/

## Project Overview

Given an array of integers `nums` and an integer `target`, return the indices of the two numbers that add up to the target. You may assume each input has exactly one solution, and you cannot use the same element twice.

## Repository Information

**Git Repository Name**: `11402_CS351_Project0`

## Implementation Scenarios

You must implement two solutions:

1. **TwoSumArray**: Brute force approach using nested loops
2. **TwoSumHashTable**: Optimized approach using a hash table

## Key Learning Objectives

- Understand trade-offs between time and space complexity
- Write effective unit tests for edge cases
- Practice AI-assisted code generation and review
- Compare algorithm efficiency

## Requirements

- Implement both `TwoSumArray()` and `TwoSumHashTable()` functions
- Design comprehensive test cases covering:
    - Normal cases
    - Edge cases (duplicates, negative numbers, etc.)
    - Boundary conditions
- Document time and space complexity for each approach
- Write clean, well-commented code
- Set up CI/CD pipeline using GitHub Actions
    - Automated testing for both `TwoSumArray()` and `TwoSumHashTable()` implementations
    - Run unit tests on every push and pull request
- Package the solution using Docker
    - Create a Dockerfile for containerized deployment
    - Include test execution in the Docker build process

## Complexity Analysis

Analyze and document:
- **TwoSumArray**: O(n²) time, O(1) space
- **TwoSumHashTable**: O(n) time, O(n) space

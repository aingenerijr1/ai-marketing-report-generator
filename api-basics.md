# API Basics

## Purpose
This file explains the basic API concepts used in the AI Marketing Performance Report Generator project.

The goal is to understand how data can move between Google Sheets, n8n, an AI model, and a report output.

## What Is an API?

An API is a way for one system to communicate with another system.

In this project, an API could allow n8n to send marketing performance data to an AI model and receive a generated report in return.

## API Request

An API request is the message sent to another system.

Example:
n8n sends marketing report data to an AI model.

## API Response

An API response is the message sent back.

Example:
The AI model sends back a weekly marketing performance report.

## GET Request

A GET request asks for information.

Plain-English example:
"Give me the latest report data."

Possible project use:
n8n reads data from a spreadsheet or another system.

## POST Request

A POST request sends information.

Plain-English example:
"Here is the marketing data. Please generate a report."

Possible project use:
n8n sends the final prompt or JSON data to an AI model.

## JSON and APIs

APIs often use JSON because it keeps data organized.

Example:

```json
{
  "metric": "users",
  "previousWeek": 1250,
  "currentWeek": 1390,
  "direction": "increase"
}

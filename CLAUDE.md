# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a documentation repository called "awesome-claude-code-tips" containing comprehensive guidance for effective Claude Code usage. The repository contains:

- `README.md` - Complete guide to Claude Code tips, session management, and workflows
- `example-workflow.md` - Detailed end-to-end example of git/GitHub workflows with Claude Code
- `CLAUDE.md` - Project-specific guidance for this repository

## Repository Purpose

This repository serves as a knowledge base and reference for developers using Claude Code. It's not a code project but rather a collection of best practices, workflows, and tips for effective AI-assisted development.

## Git Workflow

Before implementing new features or functionality, create a new feature branch following the global instructions in ~/.claude/CLAUDE.md.

## Project Structure

The repository structure will need to be established based on the chosen technology stack and project requirements.

## Claude Code Session Management

**Context Persistence:**
- CLAUDE.md is automatically read at session start
- Project files persist between sessions
- Conversation history is cleared when session ends
- Each session starts fresh with file-based context

**Updating CLAUDE.md:**
- Ask to "update CLAUDE.md" during conversation to capture new context
- Include new build commands, architecture decisions, or project setup
- Best practice: update before ending session to preserve context for next time
- Keep focused on project-specific information, avoid generic advice

**Session Lifecycle:**
- Start: Reads CLAUDE.md and project files
- Active: Maintains conversation memory and file access
- End: Clears conversation memory, keeps files intact
- Next session: Starts fresh with updated CLAUDE.md context
# nestjs-ory-kratos

NestJS and ORY Kratos Seamless Integration

## Installation

```sh
npm i @ory/client @devpulse/nestjs-ory-kratos
```

## Quick start example

Create you own auth guard:

```ts
import { Injectable } from '@nestjs/common';
import { OryAuthGuard, createUserDecorator } from '@devpulse/nestjs-ory-kratos';

@Injectable()
export class CookieAuthGuard extends OryAuthGuard() {}

export const User = createUserDecorator();

export type { Identity as UserIdentity } from '@ory/client';
```

Use guard in controller:
```ts
import { Controller, Get, Request, UseGuards } from '@nestjs/common';
import { CookieAuthGuard, User, type UserIdentity } from './auth';

@Controller()
export class AppController {
  @UseGuards(CookieAuthGuard)
  @Get('profile')
  getProfile(@User() user: UserIdentity) {
    return user;
  }
}
```
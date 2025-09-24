# nestjs-ory-kratos

NestJS and ORY Kratos Seamless Integration

## Installation

```sh
npm i @ory/client @devpulse/nestjs-ory-kratos
```

## Quick start example

Cookie authentication:

```ts
import {
  Controller,
  Get,
  Request,
  UseGuards,
  Injectable,
} from "@nestjs/common";
import { OryAuthGuard, createUserDecorator } from "@devpulse/nestjs-ory-kratos";
import type { Identity as UserIdentity } from "@ory/client";

// Is it better to move CookieAuthGuard and User to separated file
@Injectable()
export class CookieAuthGuard extends OryAuthGuard() {}
export const User = createUserDecorator();

@Controller()
export class AppController {
  @UseGuards(CookieAuthGuard)
  @Get("profile")
  getProfile(@User() user: UserIdentity) {
    return user;
  }
}
```

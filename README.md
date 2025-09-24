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
  Injectable,
  UseGuards,
  Session,
} from "@nestjs/common";
import { OryAuthGuard } from "@devpulse/nestjs-ory-kratos";
import type { Session as KratosSession } from "@ory/client";

@Injectable()
export class CookieAuthGuard extends OryAuthGuard {}

@Controller()
export class AppController {
  @UseGuards(CookieAuthGuard)
  @Get("profile")
  getProfile(@Session() session: KratosSession) {
    return session.identity;
  }
}
```
